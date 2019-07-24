---
title: 了解混合现实的性能
description: 有关优化 Windows Mixed Reality 应用的性能的高级主题和详细信息
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, 混合现实, 虚拟现实, VR, 先生, 性能, 优化, CPU, GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548826"
---
# <a name="understanding-performance-for-mixed-reality"></a>了解混合现实的性能

本文介绍了合理化混合现实应用性能的重要性。  如果你的应用程序未以最佳帧速率运行, 则用户体验会大幅降低。 全息影像看起来不稳定, 并且头跟踪的环境不准确, 导致用户体验不佳。 事实上, 必须将性能视为用于混合现实开发的第一类功能, 而不是稳定、循环结束任务。

为了查看, 下面列出了每个目标平台的高性能帧速率值。

| 平台 | 目标帧速率 |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality 超 Pc](immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality Pc](immersive-headset-hardware-details.md) | 60 FPS |

下图提供了有关最佳实践的一般概述, 并提供了接近目标帧速率的理解。 若要深入了解详细信息, 请考虑阅读[有关 Unity 的性能建议一文](performance-recommendations-for-unity.md)。 具体而言, 本文将讨论如何测量 Unity Windows Mixed Reality 应用中的帧速率, 以及在 Unity 环境中采取的步骤来提高性能。

## <a name="understanding-performance-bottlenecks"></a>了解性能瓶颈

如果你的应用程序具有绩效不佳的帧速率, 则第一步是分析并了解应用程序的计算工作量。 有两个主要处理器负责呈现场景: CPU 和 GPU。 这两个组件分别处理混合现实应用的不同操作和阶段。 有三个关键地方可能出现瓶颈。 

1. **应用线程-CPU** -此线程负责应用逻辑。 这包括处理输入、动画、物理学以及其他应用逻辑/状态
2. **将线程 CPU 呈现为 gpu** -此线程负责将绘图调用提交到 gpu。 当应用程序想要呈现某个对象 (如多维数据集或模型) 时, 此线程会将请求发送到 GPU, 该 GPU 具有为呈现进行了优化的体系结构, 以便执行这些操作。
3. **GPU**- 
   此处理器最常见地处理应用程序的图形管道, 以将3d 数据 (模型、纹理等) 转换为像素, 并最终生成一个要提交到设备屏幕的二维图像。

![帧的生存期](images/lifetime-of-a-frame.png)

通常情况下, HoloLens 应用程序将受到 GPU 限制。 但是, 这并不是每个应用程序中的 true, 因此建议使用下面的工具 & 技术来实现特定应用程序的基础。

## <a name="how-to-analyze-your-application"></a>如何分析应用程序

有许多工具可让你作为开发人员了解混合现实应用程序的性能配置文件。 这样, 你就可以在具有瓶颈的目标位置, 还可以 manifesting 自己对它们进行调试。

这是一系列常用且功能强大的工具, 用于获取应用程序的深入分析信息。
- [Intel 图形性能分析器](https://software.intel.com/gpa)
- [Visual Studio 图形调试器](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity 探查器](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 框架调试器](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>如何在任何环境中进行分析

有一个简单的测试, 可以快速确定你的应用程序中是否有可能会限制 GPU 界限或 CPU。 如果减少了渲染器目标输出的分辨率, 则需要计算的像素越少, 因此, 在呈现图像时 GPU 需要执行的工作量就越少。 视区缩放 (动态分辨率缩放) 是指将图像呈现到较小的呈现器目标, 然后显示输出设备的做法。 设备将从较小的一组像素向上采样, 以显示最终图像。

减少呈现分辨率后, 如果:
1) 应用程序的帧速率**增加**, 则可能会**限制 GPU**
1) 应用程序的帧速率**未更改**, 则可能会**限制 CPU**

>[!NOTE]
>Unity 提供了可以轻松地修改在运行时通过应用程序的呈现器目标分辨率 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性。 设备上提供的最终映像具有固定的分辨率。 平台将采样低分辨率输出, 以生成更高分辨率的图像, 以便在显示时呈现。 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>如何改进应用程序

### <a name="cpu-performance-recommendations"></a>CPU 性能建议

通常, 在 CPU 上混合现实应用程序中的大部分工作都涉及到执行场景的 "模拟" 并处理大量的唯一应用程序逻辑。 因此, 通常将以下方面作为优化目标。

- Animations
- 简化物理学
- 内存分配
- 复杂算法 (即 反向运动, 路径查找)

### <a name="gpu-performance-recommendations"></a>GPU 性能建议

#### <a name="understanding-bandwidth-vs-fill-rate"></a>了解带宽与填充率
在 GPU 上呈现帧时, 应用程序通常会被内存带宽或填充速率限制。

- **内存带宽**是 GPU 可以从内存执行的读取和写入速率
    - 若要确定带宽限制, 请降低纹理质量并检查是否改进了帧速率。
    - 在 Unity 中, 这可以通过在 "**编辑** > **项目设置** >  **[质量" 设置](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 中更改**纹理质量**来实现。
- **填充速率**是指每秒可以通过 GPU 绘制的呈现像素的吞吐量。
    - 若要确定填充速率限制, 请减小显示分辨率, 并检查是否已提高速度。 
    - 在 Unity 中，这可以通过完成 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性

内存带宽一般涉及优化到
1) 降低纹理分辨率
2) 利用更少纹理 (即 法线、镜面等)

填充速率主要侧重于减少需要针对最终呈现的像素进行计算的操作的数量。 这通常会降低
1) 要呈现/处理的对象数
2) 每个着色器的操作数
3) 到最终结果的 GPU 阶段数 (几何着色器、后处理效果等)
4) 要呈现的像素数 (即 显示分辨率)

#### <a name="reduce-poly-count"></a>减少 poly 计数
较大的多边形计数会导致更多的 GPU 操作, 减少场景中的多边形数量将减少渲染该几何的时间。 还涉及到其他因素, 这会使几何保持较高的成本, 但多边形计数是确定场景呈现的成本的基本指标。

#### <a name="limit-overdraw"></a>限制过度绘制

当呈现多个对象但该对象被另一个 (通常是更接近的 occluding 对象) 隐藏时, 将会出现高过度绘制。 想象一下, 看看有多个房间和几何的墙壁。 所有几何都将针对呈现进行处理, 但不透明的墙壁确实需要呈现, 因为它 occludes 了所有其他内容的视图。 这会导致不会浪费当前视图所需的操作。

#### <a name="shaders"></a>着色器

着色器是在 GPU 上运行的小程序, 通常确定要呈现的两个重要步骤:
1) 应在屏幕上绘制哪个对象的顶点以及它们在屏幕空间中的位置 (例如 顶点着色器)
    - 对于每个 GameObject, 顶点着色器通常按顶点执行
2) 如何为这些像素着色 (即 像素着色器)
    - 对于为设备呈现的纹理, 将为每个像素执行像素着色器

通常, 着色器会执行许多转换和照明计算。 尽管复杂的照明模型、阴影和其他操作可能会产生极好的结果, 但它们也具有价格。 减少着色器中计算的操作数可大大减少每帧 GPU 需要完成的总体工作。

##### <a name="shader-coding-recommendations"></a>着色器编码建议

- 尽可能使用双线性筛选
- 重新排列表达式以使用 MAD 内部函数, 以便同时执行相乘和 add 操作
- 在 CPU 上尽可能 Precalculate, 并将其作为常量传递给材料
- **优选从像素着色器移动到顶点着色器的操作**
    - 通常, 顶点的 < < 的像素数 (即 720p = = 921600 像素, 1080p = = 2073600 像素, 等等)

#### <a name="remove-gpu-stages"></a>删除 GPU 阶段
后期处理效果可能非常昂贵, 并且通常会阻止应用程序的填充率。 这还包括诸如 MSAA 这样的抗锯齿技术。 在 HoloLens 上, 建议完全避免使用这些方法。 此外, 如果可能, 应尽可能避免其他着色器阶段, 如几何、球面和计算着色器。

## <a name="memory-recommendations"></a>内存建议
内存分配过多 & 释放操作可能对全息应用程序产生不利影响, 从而导致性能不一致、冻结帧和其他不利行为。 在 Unity 中进行开发时, 了解内存的注意事项尤其重要, 因为内存管理由垃圾回收器控制。

#### <a name="object-pooling"></a>对象池

对象池是一种常用技术, 可降低对象 & 释放的持续分配成本。 这是通过以下方式实现的: 分配一个较大的相同对象池, 并重新使用此池中的非活动可用实例, 而不是随着时间推移不断地生成和销毁对象。 对象池非常适合在应用过程中具有可变生存期的重复使用的组件。

## <a name="see-also"></a>请参阅
- [针对 Unity 的性能建议](performance-recommendations-for-unity.md)
- [建议用于 Unity 的设置](recommended-settings-for-unity.md)
