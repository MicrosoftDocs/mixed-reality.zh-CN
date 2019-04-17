---
title: 资产创建过程
description: 创建混合的现实体验的资产的指导。
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: 资产、 创建、 进程、 预算、 多边形、 纹理、 着色器性能
ms.openlocfilehash: cec689ab4d44591d2d3e84679c3fe51dba161bc5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592990"
---
# <a name="asset-creation-process"></a>资产创建过程

Windows Mixed Reality 基于数十年的 Microsoft 提供了到 DirectX 的投资。 这意味着所有的经验和技能的开发人员必须构建 3D 图形仍然是与 HoloLens 有价值。

为项目创建的资产有多种形式和窗体。 它们可以包含一系列的纹理/图像、 音频、 视频、 三维模型和动画。 我们无法开始介绍可用于创建不同类型的资产使用在项目中的所有工具。 本文中我们将重点介绍 3D 资产创建方法。

![概念、 创建、 集成和迭代的流](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*概念、 创建、 集成和迭代的流*

## <a name="things-to-consider"></a>注意事项

当查看想要创建的体验将其作为**预算**花费以尝试创建最佳体验。 数量不一定是硬性限制**多边形**或**类型的材料**在你的资产，但更权衡一预算的组中使用。

下面是示例预算为你的体验。 性能通常不是单点故障，但通过千位切割每-se 死亡。
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>资产</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> 内存</th>
</tr><tr>
<td> 多边形</td><td> 0%</td><td> 5%</td><td> 10%</td>
</tr><tr>
<td> 纹理</td><td> 5%</td><td> 15%</td><td>25%</td>
</tr><tr>
<td> 着色器</td><td> 15%</td><td> 35%</td><td> 0%</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> 物理引擎</td><td> 5%</td><td> 15%</td><td> 0%</td>
</tr><tr>
<td> 实时照明</td><td> 10%</td><td> 0%</td><td> 0%</td>
</tr><tr>
<td> 媒体 （音频/视频）</td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> 脚本/逻辑</td><td> 25%</td><td> 0%</td><td> 5%</td>
</tr><tr>
<td> 常规的开销</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>总计</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**资产的总数**
* 场景中处于活动状态多少资产？

**资产的复杂性**
* 多少三角形 / 多边形？
* 复杂程度是着色器？

开发人员和艺术家不得不考虑设备和图形引擎的功能。 Microsoft HoloLens 具有所有的计算和图形内置于该设备。 它会共享开发人员会发现在移动平台的功能。

资产创建过程是相同的无论您的目标的体验如何[holographic 的设备或沉浸式设备](mixed-reality.md#the-mixed-reality-spectrum)。 需要注意的主要事项就是设备功能，以及缩放如上所述，由于可以在想要维护正确的缩放范围基于体验的混合现实中看到现实世界。 

## <a name="authoring-assets"></a>创作资产

我们将开始为你的项目资产中获取的方法：
1. 创建资产 （创作工具和对象捕获）
2. 购买资产 （联机购买资产）
3. 移植资产 （使用现有的资产）
4. 外包资产 （从第三方导入资产）

### <a name="creating-assets"></a>创建资产

**创作工具**<br>
首先可以通过多种不同的方式创建你自己的资产。 3D 艺术家使用大量的应用程序和工具创建模型组成**网格**，**纹理**，并**材料**。 这随后保存的文件格式，可以导入或图形引擎由应用程序中，如使用 **。FBX**或 **。OBJ**。 任何工具，可生成所选的图形引擎支持的模型将着手**HoloLens**。 在 3D 艺术家之间很多选择使用[Autodesk Maya 本身是能够使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA)要转换的方法创建资产。 如果你想要在快速获取内容还可以使用[3D 生成器](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)随附 Windows 导出。在你的应用程序中使用 OBJ。

**对象捕获**<br>
此外，还有选项以捕获以三维形式的对象。 捕获在 3D 死气沉沉和编辑其数字内容创建软件是 3D 打印的发展越来越受欢迎。 使用**Kinect 2**传感器和[3D 生成器](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)可以使用捕获功能从现实世界对象创建资产。 这也是[的工具套件](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software)执行与相同**photogrammetry**通过处理一些拼接在一起和网格与纹理的图像。

### <a name="purchasing-assets"></a>购买资产

另一个极好的选择是购买你的体验的资产。 有大量的资产可通过服务如[Unity 资产商店](https://www.assetstore.unity3d.com/)或[TurboSquid](http://www.turbosquid.com/)等等。

当从第三方购买资产时始终想要检查以下各项：
* **什么是多边形计数？**
  * 它是否适合你的预算？
* **是否有级别 (Lod) 的模型的详细信息？**
  * 模型的详细信息级别，可缩放的性能的模型的详细信息。
* **源文件是否可用？**
  * 通常不包括在[Unity 资产商店](https://www.assetstore.unity3d.com/)始终附带等服务，但[TurboSquid](http://www.turbosquid.com/)。
  * 没有源代码文件的情况下你将无法修改资产。
  * 请确保你 3D 工具可以导入提供的源代码文件。
* **知道您得到什么**
  * 提供了动画？
  * 请务必检查您打算购买的资产的内容列表。

### <a name="porting-assets"></a>移植资产

在某些情况下将传递为其他设备和不同的应用程序最初生成的现有资产。 在大多数情况下这些资产可以转换为使用自己的应用程序的图形引擎与兼容的格式。

移植资产 HoloLens 应用程序中使用时，想要询问以下：
* **可以在直接导入或确实需要转换为另一种格式？** 检查要与图形引擎使用导入的格式。
* **如果将转换为兼容的格式是任何内容丢失？** 有时可能会丢失的详细信息，或导入可能会导致需要清理 3D 创作工具中的项目。
* **什么是三角形/多边形计数为资产？** 根据为应用程序可以使用预算[Simplygon](https://www.simplygon.com/)或类似的工具来竞技 （虽然或手动减小多边形计数） 原始的资产，以适合你的应用程序的预算。

### <a name="outsourcing-assets"></a>外包资产

需要多个资产比你的团队的较大项目的另一个选项是能够创建是外包资产创建。 外包的过程涉及到查找正确的 studio 或专门的机构外包资产中。 这可以最高的选项，但也是最灵活中获得的内容。
* **清楚地定义您的请求**
  * 尽量提供详尽的信息
  * 前端、 端和后的概念图像
  * 在上下文中引用艺术显示资产
  * （通常以厘米为单位指定） 的对象的小数位数
* **提供预算**
  * 多边形计数范围
  * 纹理数
  * 类型的着色器 （用于 Unity 和 HoloLens 您应始终默认为移动着色器第一次）
* **了解产生的成本**
  * 更改请求的外包策略是什么？

外包可特别适合基于项目时间线上，但需要更多的监督功能，可保证获得正确的资产需要第一次。
