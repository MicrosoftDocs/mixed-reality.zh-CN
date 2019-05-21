---
title: 混合现实的了解性能
description: 优化 Windows 混合现实应用程序的性能上的高级主题和详细信息
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows 混合现实、 混合的现实中，虚拟现实、 VR、 MR、 性能、 优化、 CPU、 GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592659"
---
# <a name="understanding-performance-for-mixed-reality"></a>混合现实的了解性能

本文将介绍到合理化 for Mixed Reality 应用性能的重要性。  如果你的应用程序不会运行以获得最佳的帧速率，可以极大地降低用户体验。 全息将出现不稳定，头环境的跟踪将不准确导致体验不佳的用户。 实际上，作为混合现实开发并不稳定、 周期任务的末尾的第一个类功能，必须考虑性能。

查看，下面列出了每个目标平台的高性能帧速率值。

| 平台 | 目标帧速率 |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality Ultra Pc](immersive-headset-hardware-details.md) | 90 FPS |
| [混合现实 Pc 的 Windows](immersive-headset-hardware-details.md) | 60 FPS |

下面的框架为一般摘要提供了有关的最佳实践和理解针对达到目标帧速率。 若要深入了解更多详细信息，可以考虑阅读[Unity 项目的性能建议](performance-recommendations-for-unity.md)。 具体而言，此相关的文章将讨论如何测量 Unity Windows Mixed Reality 应用以及要在 Unity 环境中执行以提高性能的步骤中的帧速率。

## <a name="understanding-performance-bottlenecks"></a>了解性能瓶颈

如果你的应用程序性能不佳的帧速率，第一步是分析并了解你的应用程序是计算密集型操作。 有两个主要处理器负责的工作来呈现您的场景： CPU 和 GPU。 这两个组件的每个处理不同的操作和混合现实应用程序的阶段。 有三个密钥的位置可能会出现瓶颈。 

1. **应用程序线程的 CPU** -此线程负责你的应用逻辑。 这包括处理输入、 动画、 物理特性、 和其他应用程序逻辑/状态
2. **呈现线程的 CPU 与 GPU** -此线程负责提交到 GPU 在绘图调用。 当您的应用程序想要呈现的对象例如多维数据集或模型时，此线程将请求发送到 GPU，其中的优化，以便呈现体系结构，以执行这些操作。
3. **GPU** - 
   此处理器最常处理图形管道的应用程序 （模型、 纹理等） 的 3D 数据转换为像素，并最终生成 2D 图像提交到你的设备的屏幕。

![框架的生存期](images/lifetime-of-a-frame.png)

通常情况下，HoloLens 应用程序将有限的 GPU。 但是，这不保存在每个应用程序中，则返回 true，因此建议使用工具和技术如下回到地面点真实成分为特定应用。

## <a name="how-to-analyze-your-application"></a>如何分析应用程序

有许多工具，它们可以作为开发人员了解混合现实应用程序的性能配置文件。 这使您能够通过了瓶颈和如何它们都表现形式本身来对其进行调试这两个目标。

这是一系列流行且强大的工具，以获取你的应用程序的深入分析信息。
- [Intel Graphics Performance Analyzers](https://software.intel.com/gpa)
- [Visual Studio 图形调试器](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 框架调试器](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>如何在任何环境中的配置文件

没有简单的测试来快速确定你是否有可能 GPU 绑定或 CPU 绑定应用程序中。 如果减少呈现器目标输出的分辨率，有更少的像素为单位计算，因此，工作较少 GPU 需要执行以呈现图像。 视区缩放 （动态解析缩放） 是呈现到较小的映像的做法是呈现器目标，然后输出设备可以显示。 设备将最多的示例从较小的集要显示最终图像的像素。

之后如果减少呈现解决方法：
1) 应用程序帧速率**增加**，那么您就有可能**GPU 界定**
1) 应用程序帧速率**保持不变**，那么您就有可能**CPU 绑定**

>[!NOTE]
>Unity 提供了可以轻松地修改在运行时通过应用程序的呈现器目标分辨率 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性。 最终图像显示在设备上具有固定的分辨率。 该平台将示例输出以生成在显示器上呈现的更高分辨率图像的较低分辨率。 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>如何提高你的应用程序

### <a name="cpu-performance-recommendations"></a>CPU 性能建议

通常情况下，在 CPU 上的混合的现实应用程序中的大部分工作涉及执行"模拟"的场景和处理大量唯一的应用程序逻辑。 因此，以下几个方面通常针对优化。

- Animations
- 简化的物理
- 内存分配
- 复杂的算法 （即 反向运动学、 路径查找）

### <a name="gpu-performance-recommendations"></a>GPU 性能建议

#### <a name="understanding-bandwidth-vs-fill-rate"></a>了解带宽 vs 的填充率
当呈现在 GPU 上的帧，应用程序是通常是由内存带宽或填充率绑定。

- **内存带宽**是读取操作的速率和 GPU 可以执行从内存写入
    - 若要确定带宽限制，减少纹理质量，并检查是否有所改善帧速率。
    - 在 Unity 中，这可以通过更改**纹理质量**中**编辑** > **项目设置** >   **[质量设置](https://docs.unity3d.com/Manual/class-QualitySettings.html)**。
- **填充率**指的是呈现可由 GPU 每秒绘制的像素为单位的吞吐量。
    - 若要标识填充速率限制，降低显示分辨率和检查帧速率是否有所改善。 
    - 在 Unity 中，这可以通过完成 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性

内存带宽通常涉及到为优化
1) 减少纹理的解决方法
2) 使用更少的纹理 （即 法线，反射高光，等等）

填充率主要致力于减少需要为最终呈现像素计算的操作的数目。 此示例通常划分为减少
1) 要呈现/处理的对象数
2) 每个着色器的操作数
3) GPU 阶段到最终结果 （几何着色，后处理效果，等等） 的数目
4) 要呈现 （即的像素数 显示分辨率）

#### <a name="reduce-poly-count"></a>减少 poly 计数
减少您的场景中的多边形的数量将减少的时间来呈现该几何图形和更高版本的多边形计数中的 GPU 的更多操作的结果。 还有其他一些因素也参与明暗度的几何图形，它仍可能很昂贵，但会多边形计数的基本度量指标来确定如何昂贵场景会呈现。

#### <a name="limit-overdraw"></a>限制过度绘制

高过度绘制多个对象都呈现，但不是输出到屏幕，因为它们隐藏的另一个的通常接近 occluding 对象时发生。 假设在墙上具有多个房间和其后的几何图形的查找。 将呈现为处理所有的几何图形，但仅不透明墙上插座真正需要进行的呈现将如 occludes 所有其他内容的视图。 这会导致不需要的当前视图的必要操作。

#### <a name="shaders"></a>着色器

着色器是小程序中，在 GPU 上运行，并通常确定呈现中的两个重要步骤：
1) 应在屏幕和，并在屏幕空间 （即上绘制的对象的顶点 顶点着色器）
    - 适用于每个 GameObject 中，将顶点着色器通常执行每顶点
2) 内容 （即，这些像素的颜色 像素着色器）
    - 像素着色器执行每个像素呈现为设备存在的纹理

着色器，通常执行很多转换和照明计算。 尽管复杂照明模型、 阴影和其他操作可以生成出色的结果，但它们还会附带一个价格。 减少的计算着色器中的操作可以极大地降低由每个框架的 GPU 执行所需的整体工作。

##### <a name="shader-coding-recommendations"></a>着色器编码的建议

- 使用双线性筛选，只要有可能
- 重新排列表达式才能执行乘法和 add 操作在同一时间使用 MAD 内部函数
- 要尽可能多地在 CPU 上预先计算并将其作为常量传递到材料
- **倾向于从像素着色器向顶点着色器的移动操作**
    - 通常的顶点 # << # 像素 （即 720p = = 921,600 像素，1080p = = 2,073,600 像素为单位，等等)

#### <a name="remove-gpu-stages"></a>删除 GPU 阶段
后期处理效果可以开销非常大并通常会禁止您的应用程序的填充率。 这还包括抗锯齿技术，如 MSAA。 上 HoloLens，建议完全避免这些技术。 此外，如果可能，应避免额外的着色器阶段，如几何图形、 外壳，并计算着色器。

## <a name="memory-recommendations"></a>内存建议
过多的内存分配和解除分配操作可以产生负面影响，从而导致不一致的性能、 冻结的框架和其他造成不利影响的行为在全息版应用程序上。 它是由于内存管理控制垃圾回收器在 Unity 中进行开发时了解内存注意事项尤为重要。

#### <a name="object-pooling"></a>对象池

对象池是一种常用的方法，以降低成本的连续分配和释放的对象。 这是通过分配完全相同的对象的大型池和重新使用从这个池而不是不断地生成和随着时间的推移销毁对象的非活动状态、 可用的实例。 对象池非常适合用于具有变量的生存期期间应用的可重用组件。

## <a name="see-also"></a>请参阅
- [Unity 的性能建议](performance-recommendations-for-unity.md)
- [Unity 的推荐的设置](recommended-settings-for-unity.md)
