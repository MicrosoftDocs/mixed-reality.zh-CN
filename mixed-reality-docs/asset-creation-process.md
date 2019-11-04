---
title: 资产创建过程
description: 有关为混合现实体验创建资产的指导。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: 资产，创建，处理，预算，多边形，纹理，着色器，性能
ms.openlocfilehash: fb8266a018e11a8fb944819a0cac5ace38f2cb25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437010"
---
# <a name="asset-creation-process"></a>资产创建过程

Windows Mixed Reality 构建于 Microsoft 投入了 DirectX 的数十年中。 这意味着，开发人员构建3D 图形的所有经验和技能都将继续对 HoloLens 有用。

你为项目创建的资产分为多个形状和窗体。 它们可以包含一系列纹理/图像、音频、视频、3D 模型和动画。 我们无法开始涵盖可用于创建项目中使用的不同类型资产的所有工具。 对于本文，我们将重点介绍3D 资产创建方法。

![概念、创建、集成和迭代流](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*概念、创建、集成和迭代流*

## <a name="things-to-consider"></a>注意事项

在观看您的体验时，您要尝试创建它作为**预算**，以尝试创建最佳体验。 不一定会对资产中的**多边形**数量或**材料类型**的数量有硬性限制，但会有一组预算的折衷。

下面是你的体验的示例预算。 性能通常不是单一故障点，而是每 se 一千次切削死亡。
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>标号</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> 内存</th>
</tr><tr>
<td> 多边形</td><td> 0</td><td> 5</td><td> 万</td>
</tr><tr>
<td> 纹理</td><td> 5</td><td> 15</td><td>25%</td>
</tr><tr>
<td> 着色器</td><td> 15</td><td> 35%</td><td> 0</td>
</tr><tr>
<td> <b>Ax</b></td><td></td><td></td><td></td>
</tr><tr>
<td> 物理</td><td> 5</td><td> 15</td><td> 0</td>
</tr><tr>
<td> 实时照明</td><td> 万</td><td> 0</td><td> 0</td>
</tr><tr>
<td> 媒体（音频/视频）</td><td> -</td><td> 15</td><td> 25%</td>
</tr><tr>
<td> 脚本/逻辑</td><td> 25%</td><td> 0</td><td> 5</td>
</tr><tr>
<td> 一般开销</td><td> 5</td><td> 5</td><td> 5</td>
</tr><tr>
<td> <b>总</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**资产总数**
* 场景中有多少资产处于活动状态？

**资产复杂性**
* 三角形/多边形有多少？
* 着色器的复杂程度如何？ 使用混合现实工具包时，建议使用[混合现实工具包标准着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)来降低着色器的复杂性。

开发人员和艺术家都必须考虑设备和图形引擎的功能。 Microsoft HoloLens 包含内置于设备中的所有计算和图形。 它共享开发人员在移动平台上所能找到的功能。

无论您的目标是[全息设备还是沉浸式设备](mixed-reality.md#the-mixed-reality-spectrum)的体验，资产的创建过程都是相同的。 需要注意的主要事项是上述设备功能以及规模，因为你可以在混合现实中看到真实世界，你需要根据经验维护适当的规模。 

## <a name="authoring-assets"></a>创作资产

首先，我们将介绍如何获取项目的资产：
1. 创建资产（创作工具和对象捕获）
2. 购买资产（联机购买资产）
3. 移植资产（获取现有资产）
4. 外包资产（从第三方导入资产）

### <a name="creating-assets"></a>创建资产

**创作工具**<br>
首先，您可以使用多种不同的方法创建自己的资产。 三维音乐家使用多种应用程序和工具来创建由**网格**、**纹理**和**材料**组成的模型。 然后以文件格式保存该文件，应用程序使用的图形引擎可以导入或使用该格式，如 **。FBX**或 **。OBJ**。 生成所选图形引擎支持的模型的任何工具将在**HoloLens**上运行。 在三维音乐家之间，很多选择使用[Autodesk 的 Maya，它本身能够使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA)来转换资产的创建方式。 如果你想要快速获取内容，还可以使用随 Windows 一起导出的[3D 生成器](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)。要在应用程序中使用的 OBJ。

**对象捕获**<br>
还可以选择在三维中捕获对象。 在三维中捕获 inanimate 对象并通过数字内容创建软件对其进行编辑时，三维打印增加了。 使用**Kinect 2**传感器和[3d 生成器](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)，可以使用捕获功能从真实世界对象创建资产。 这也是一[套工具](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software)，用于通过处理多个要装订在一起以及网格和纹理的图像来对**photogrammetry**执行相同的操作。

### <a name="purchasing-assets"></a>采购资产

另一种极佳的选择是购买资产以获得经验。 有大量的资产可通过[Unity 资产存储区](https://www.assetstore.unity3d.com/)或[TurboSquid](https://www.turbosquid.com/)等服务获得。

从第三方购买资产时，始终需要检查以下各项：
* **什么是 poly 计数？**
  * 它是否适用于预算内？
* **是否有针对该模型的详细信息（LODs）？**
  * 利用模型的详细信息级别，可以缩放模型的详细信息以提高性能。
* **源文件可用吗？**
  * 通常不包含在[Unity 资产存储区](https://www.assetstore.unity3d.com/)中，但始终包含在[TurboSquid](https://www.turbosquid.com/)等服务中。
  * 如果没有源文件，将无法修改资产。
  * 请确保3D 工具可以导入提供的源文件。
* **了解所获得的内容**
  * 动画是否提供？
  * 请确保检查要购买的资产的 "内容" 列表。

### <a name="porting-assets"></a>移植资产

在某些情况下，你将获得最初为其他设备和不同应用生成的现有资产。 在大多数情况下，可以将这些资产转换为与应用正在使用的图形引擎兼容的格式。

在将资产移植到 HoloLens 应用程序中使用时，需要询问以下内容：
* **能否直接导入或是否需要将其转换为另一种格式？** 使用正在使用的图形引擎检查要导入的格式。
* **如果转换为兼容的格式，会丢失任何内容吗？** 有时，详细信息可能会丢失，或者导入可能会导致需要在三维创作工具中清除的项目。
* **资产的三角形/多边形数是多少？** 根据你的应用程序的预算，你可以使用[Simplygon](https://www.simplygon.com/)或类似的工具来 decimate （过程或手动缩减 poly 计数）原始资产，使其适合你的应用程序预算。

### <a name="outsourcing-assets"></a>外包资产

对于需要更多资产而不是团队创建的大型项目，另一个选项是将资产创建外包。 外包过程涉及到寻找适用于外包资产的正确工作室或机构。 这可能是成本最高的选项，但也是最灵活的选项。
* **明确定义你请求的内容**
  * 提供尽可能多的详细信息
  * 正面、反面和背面概念图像
  * 显示上下文中资产的参考资料
  * 对象的小数位数（通常以厘米为单位指定）
* **提供预算**
  * Poly 计数范围
  * 纹理数量
  * 着色器的类型（适用于 Unity 和 HoloLens，应始终首先默认为移动着色器）
* **了解成本**
  * 更改请求的外包策略是什么？

外包可以很好地根据项目时间线工作，但需要更多的监督来保证你首次获得所需的正确资产。
