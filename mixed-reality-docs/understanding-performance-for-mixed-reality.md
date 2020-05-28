---
title: 了解混合现实的性能
description: 有关优化 Windows Mixed Reality 应用的性能的高级主题和详细信息
author: troy-ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，性能，优化，CPU，GPU
ms.openlocfilehash: 4a0f4cd9caea5dd601ad663801e760261980c429
ms.sourcegitcommit: b0d15083ec1095e08c9d776e5bae66b4449383bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2020
ms.locfileid: "84111028"
---
# <a name="understanding-performance-for-mixed-reality"></a>了解混合现实的性能

本文介绍了如何了解混合现实应用的性能的重要性。  如果你的应用程序未以最佳帧速率运行，则用户体验会大幅降低。 全息影像会显得不稳定，因此，对环境的打印头跟踪是不准确的，导致用户体验不佳。 对于混合现实开发而言，必须将性能视为第一类功能，而不是波兰语任务。

下面列出了每个目标平台的高性能帧速率值。

| 平台 | 目标帧速率 |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality 超 Pc](immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality Pc](immersive-headset-hardware-details.md) | 60 FPS |

下面的框架概述了命中目标帧速率的最佳实践。 如果在 Unity 中进行开发，则请考虑阅读有关[unity 的性能建议一文](performance-recommendations-for-unity.md)，了解在 unity 环境中测量和提高帧率的技巧。

## <a name="understanding-performance-bottlenecks"></a>了解性能瓶颈

如果你的应用程序具有绩效不佳的帧速率，则第一步是分析并了解应用程序的计算工作量。 有两个主要处理器负责呈现场景： CPU 和 GPU。 其中每个都处理混合现实应用的不同方面。 有三个关键地方可能出现瓶颈： 

1. **应用线程-CPU** -此线程负责应用逻辑。 这包括处理输入、动画、物理学和其他应用逻辑。
2. **将线程 CPU 呈现为 gpu** -此线程负责将绘图调用提交到 gpu。 当应用程序想要呈现某个对象（如多维数据集或模型）时，此线程会将请求发送到 GPU 以执行这些操作。
3. **GPU** -此处理器最常见地处理应用程序的图形管道，以将3d 数据（模型、纹理等）转换为像素。 它最终会生成一个要提交到设备屏幕的二维图像。

![帧的生存期](images/lifetime-of-a-frame.png)

通常情况下，HoloLens 应用程序将被绑定到 GPU，但并不总是如此。 使用下面的工具和技术来了解你的特定应用程序的瓶颈所在。

## <a name="how-to-analyze-your-application"></a>如何分析应用程序

有许多工具可让你了解混合现实应用程序的性能配置文件。 这样，你就可以找到存在瓶颈的位置和原因，以便解决问题。

下面是一些常用工具，用于获取应用程序的深入分析信息：
- [Intel 图形性能分析器](https://software.intel.com/gpa)
- [Visual Studio 图形调试器](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity 探查器](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 框架调试器](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>如何在任何环境中进行分析

确定你的应用程序中是否有 GPU 界限或 CPU 限制的一种方法是降低呈现器目标输出的分辨率。 通过减少要计算的像素数，这将减少 GPU 负载。 设备将呈现为一个较小的纹理，然后显示一个示例，显示最终图像。

减少呈现分辨率后，如果：
1) 应用程序的帧速率**增加**，则可能会**绑定 GPU**
1) 应用程序的帧速率**未更改**，则可能会**绑定 CPU**

>[!NOTE]
>Unity 提供了在运行时通过*[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性轻松修改应用程序的呈现目标解析的能力。 设备上提供的最终映像具有固定的分辨率。 平台将采样低分辨率输出，以生成更高分辨率的图像，以便在显示时呈现。 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>如何改进应用程序

### <a name="cpu-performance-recommendations"></a>CPU 性能建议

通常，在 CPU 上混合现实应用程序中的大部分工作都涉及到执行场景的 "模拟" 和处理应用程序逻辑。 以下区域通常针对优化：

- 动画
- 物理
- 内存分配
- 复杂算法（即 反向运动，路径查找）

### <a name="gpu-performance-recommendations"></a>GPU 性能建议

#### <a name="understanding-bandwidth-vs-fill-rate"></a>了解带宽与填充速率
当在 GPU 上呈现帧时，应用程序通常按内存带宽或填充速率进行绑定。

- **内存带宽**是 GPU 可以从内存执行的读取和写入速率
    - 若要确定带宽限制，请降低纹理质量并检查帧速率是否已提高。
    - 在 Unity 中，这可以通过在 "**编辑** **Texture Quality**  >  **项目设置**  >  **[质量" 设置](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 中更改纹理质量来实现。
- **填充速率**是指每秒可以通过 GPU 绘制的像素。
    - 若要确定填充速率限制，请减小显示分辨率，并检查是否已提高速度。 
    - 在 Unity 中，可以通过*[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性完成此操作

内存带宽一般涉及优化到以下任一操作：
1) 降低纹理分辨率
2) 利用更少纹理（法线、镜面等）

填充速率侧重于减少需要针对最终呈现的像素进行计算的操作的数量。 这包括减少：
1) 要呈现/处理的对象数
2) 每个着色器的操作数
3) 到最终结果的 GPU 阶段数（几何着色器、后处理效果等）
4) 要呈现的像素数（显示分辨率）

#### <a name="reduce-polygon-count"></a>减少多边形计数

较大的多边形计数会导致更多的 GPU 操作;[减少场景中的多边形数量](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)将减少渲染时间。 对于可能开销较大的几何图形，还涉及到其他因素，而多边形计数是确定要呈现场景的成本最高的指标。

#### <a name="limit-overdraw"></a>限制过度绘制

当显示多个对象但在屏幕上未显示过度绘制时，因为 occluding 对象隐藏了多个对象。 想象一下，看看有对象后面的墙。 所有几何都将处理以便呈现，但只需呈现不透明的墙壁。 这会导致不必要的操作。

#### <a name="shaders"></a>着色器

着色器是在 GPU 上运行的小程序，可执行以下两个重要步骤：
1) 确定应绘制的顶点以及它们在屏幕空间中的位置（顶点着色器）
    - 对于每个网格，顶点着色器通常按顶点执行。
2) 确定每个像素的颜色（像素着色器）
    - 像素着色器将由几何图形呈现的每个像素执行到所呈现的纹理。

通常，着色器会执行许多转换和照明计算。 尽管复杂的照明模型、阴影和其他操作可能会产生极好的结果，但它们也具有价格。 减少着色器中计算的操作数可以极大地减少 GPU 每帧所需的工作量。

##### <a name="shader-coding-recommendations"></a>着色器编码建议

- 尽可能使用双线性筛选
- 重新排列表达式以使用 MAD 内部函数，以便同时执行相乘和 add 操作
- 在 CPU 上尽可能 Precalculate，并将其作为常量传递给材料
- **优选从像素着色器移动到顶点着色器的操作**
    - 通常，顶点的数目要小于像素数（720p 为921600像素，1080p 为2073600像素，等等）。

#### <a name="remove-gpu-stages"></a>删除 GPU 阶段

后期处理效果可能会非常昂贵，并会提高应用程序的填充率。 这包括诸如 MSAA 这样的抗锯齿技术。 在 HoloLens 上，建议完全避免使用这些技术以及其他着色器阶段，如几何、球面和计算着色器。

## <a name="memory-recommendations"></a>内存建议

过多的内存分配和释放操作可能导致性能不一致、冻结帧以及其他不利行为。 在 Unity 中进行开发时了解内存的注意事项尤其重要，因为内存管理由垃圾回收器控制。

#### <a name="object-pooling"></a>对象池

对象池是一种常用技术，可降低对象的连续分配和释放的成本。 这是通过以下方式实现的：分配一个较大的相同对象池，并重新使用此池中的非活动可用实例，而不是随着时间推移不断地生成和销毁对象。 对象池非常适合在应用过程中具有可变生存期的重复使用的组件。

## <a name="see-also"></a>另请参阅
- [针对 Unity 的性能建议](performance-recommendations-for-unity.md)
- [建议用于 Unity 的设置](recommended-settings-for-unity.md)
- [优化3D 模型](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [转换和优化实时3D 模型的最佳做法](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)

