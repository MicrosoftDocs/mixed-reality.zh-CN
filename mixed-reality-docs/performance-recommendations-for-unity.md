---
title: 针对 Unity 的性能建议
description: 有关提高混合现实应用性能的 Unity 特定提示。
author: troy-ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 图形, cpu, gpu, 渲染, 垃圾回收, hololens
ms.localizationpriority: high
ms.openlocfilehash: 28f09986cdb8c562aedfc9deae7b0369214ebc05
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277565"
---
# <a name="performance-recommendations-for-unity"></a>针对 Unity 的性能建议

本文是在[针对混合现实的性能建议](understanding-performance-for-mixed-reality.md)中所述内容的基础上编写的，但重点介绍特定于 Unity 引擎环境的知识。

## <a name="use-recommended-unity-project-settings"></a>使用建议的 Unity 项目设置

在 Unity 中优化混合现实应用的性能时，最重要的第一步是确保使用[建议用于 Unity 的环境设置](recommended-settings-for-unity.md)。 该文中的内容涉及到一些对于生成高性能混合现实应用至关重要的场景配置。 本文也强调了其中建议的一些设置。

## <a name="how-to-profile-with-unity"></a>如何使用 Unity 进行探查

Unity 提供内置的 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** ，它是一个极佳的资源，可以收集特定应用的重要性能见解。 尽管用户可以在编辑器中运行该探查器，但这些指标并不代表真正的运行时环境，因此应该慎用其结果。 建议在设备上运行应用程序时远程对其进行探查，以获得最准确且可对其采取措施的见解。 此外，Unity 的 [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) 也是一个非常强大的见解工具。

Unity 提供了以下方面的详尽文档：
1) 如何[将 Unity Profiler 远程连接到 UWP 应用程序](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) 如何有效[使用 Unity Profiler 诊断性能问题](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> 在连接 Unity Profiler 并添加 GPU 探查器后（查看右上角的“添加探查器”），可以在探查器的中间分别查看花费在 CPU 和 GPU 上的时间。  这样，开发人员很快就能大致了解其应用程序是受 CPU 还是 GPU 的约束。
>
> ![Unity CPU 与 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU 性能建议

以下内容涵盖更深入的性能做法，特别适合在 Unity 和 C# 开发中采用。

#### <a name="cache-references"></a>缓存引用

最佳做法是在初始化时缓存对所有相关组件和 GameObject 的引用。 这是因为，与存储指针所产生的内存开销相比，重复 *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 之类的函数调用所造成的开销要高得多。 这同样适用于极度频繁使用的 [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)。 *Camera.main* 实际上在幕后只是使用 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* ，但却以很高的开销在场景图中搜索具有 *“MainCamera”* 标记的相机对象。

```CS
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    private Camera cam;
    private CustomComponent comp;

    void Start() 
    {
        cam = Camera.main;
        comp = GetComponent<CustomComponent>();
    }

    void Update()
    {
        // Good
        this.transform.position = cam.transform.position + cam.transform.forward * 10.0f;

        // Bad
        this.transform.position = Camera.main.transform.position + Camera.main.transform.forward * 10.0f;

        // Good
        comp.DoSomethingAwesome();

        // Bad
        GetComponent<CustomComponent>().DoSomethingAwesome();
    }
}
```

>[!NOTE] 
> 避免 GetComponent(string) <br/>
> 使用 *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 时，会产生少量不同的重载。 必须始终使用基于类型的实现，切勿使用基于字符串的搜索重载。 在场景中按字符串进行搜索，比按类型进行搜索的开销要高得多。 <br/>
> （正确）Component GetComponent(Type type) <br/>
> （正确）T GetComponent\<T>() <br/>
> （错误）Component GetComponent(string)> <br/>

#### <a name="avoid-expensive-operations"></a>避免高开销的操作

1) **避免使用 [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    尽管 LINQ 非常简洁且易于读写，但与手动写出算法相比，它所需的计算资源要多得多，尤其是内存分配。

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **通用 Unity API**

    某些 Unity API 虽然很有用，但其执行开销可能极高。 其中的大部分 API 都涉及到在整个场景图中搜索 GameObject 的匹配列表。 一般情况下，若要避免这些操作，可以缓存引用，或者实现相关 GameObject 的管理器组件，以在运行时跟踪引用。

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> 应该消除 *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 和 *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 的所有开销。 与直接函数调用相比，这些函数可能要慢上若干千倍。

3) **注意装箱**

    [装箱](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)是 C# 语言和运行时的核心概念。 它是将值类型化变量（例如 char、int、bool 等）包装到引用类型化变量中的过程。 将值类型化变量“装箱”后，该变量将包装在 System.Object 内，后者存储在托管堆上。 因此，需要分配内存，并在最终释放内存后，由垃圾回收器处理内存。 这种分配和解除分配会损害性能，且在许多情况下是不必要的，或者可以由开销更低的替代做法轻松取代。

    开发中最常见的装箱形式之一是使用[可为 null 值类型](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)。 开发人员经常希望能够在函数中为值类型返回 null，尤其是操作在尝试获取该值可能失败的情况下。 此方法的潜在问题是，现在分配在堆上发生，因此以后需要进行垃圾回收。

    **C# 中的装箱示例**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **通过可为 null 值类型进行装箱出现问题的示例**

    此代码演示一个可在 Unity 项目中创建的虚构粒子类。 对 `TryGetSpeed()` 的调用将导致在堆上分配对象，因此需要在以后的某个时间点进行垃圾回收。 在此示例中之所以会出现特定的问题，是因为场景中可能有 1000 个甚至更多的粒子，而函数需要查询每个粒子的当前速度。 这样，就要分配数千个对象，因而要解除分配每个帧，这会极大地降低性能。 重新编写函数以返回一个负值（例如 -1）来指示失败可以避免此问题，并在堆栈上保留内存。

    ```csharp
        public class MyParticle
        {
            // Example of function returning nullable value type
            public int? TryGetSpeed()
            {
                // Returns current speed int value or null if fails
            }
        }
    ```

#### <a name="repeating-code-paths"></a>重复代码路径

应该精心编写每秒要执行多次的任何 重复性 Unity 回调函数（例如 Update）和/或帧。 此处发生的任何高开销操作都会对性能持续造成巨大影响。

1) **空回调函数**

    在应用程序中保留以下代码看似没有妨碍，尤其是因为每个 Unity 脚本都要通过此代码块自动初始化，但这些空回调的实际开销可能非常高。 Unity 在 UnityEngine 代码与应用程序代码之间的非托管/托管代码边界范围内来回操作。 通过此桥梁进行上下文切换会产生相当高的开销，即使没有要执行的操作。 如果应用具有数百个 GameObject 以及包含空重复性 Unity 回调的组件，则此操作特别容易造成问题。

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update() 最容易造成此性能问题，但如下所列的其他重复性 Unity 回调可能也好不到哪里去，甚至更糟：FixedUpdate()、LateUpdate()、OnPostRender"、OnPreRender()、OnRenderImage() 等。 

2) **偏向于对每帧运行一次的操作**

    以下 Unity API 是许多全息应用的常用操作。 尽管并非总是可行，但这些函数的结果往往只计算一次，然后在整个应用程序中对给定的帧重新利用结果。

    a) 一般情况下，最好是通过一个专用的单一实例类或服务来处理投影到场景中的视线，然后在所有其他场景组件中重复使用此结果，而无需由每个组件执行重复性的，但本质上相同的光投影操作。 当然，某些应用程序可能要求从不同的原点投射光线，或者针对不同的[图层遮罩](https://docs.unity3d.com/ScriptReference/LayerMask.html)投射光线。

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) 通过在 Start()或 Awake() 中[缓存引用](#cache-references)，来避免重复性 Unity 回调（例如 Update()）中的 GetComponent() 操作

        UnityEngine.Object.GetComponent()

    c) 如果可能，最好是在初始化时实例化所有对象，并使用[对象池](#object-pooling)在应用程序的整个运行时中回收并重复使用 GameObject。

        UnityEngine.Object.Instantiate()

3) **避免接口和虚拟构造**

    与利用直接构造或直接函数调用相比，通过接口与直接对象调用函数或调用虚拟函数往往会造成高得多的开销。 如果不需要虚拟函数或接口，应将其删除。 但是，如果利用它们能够简化开发协作、改善代码的易读性和代码可维护性，则这些做法造成的性能下降一般是值得的。

    一般情况下，不建议将字段和函数标记为虚拟，除非明确要求覆盖此成员。 应特别注意要对每个帧调用多次（甚至对每个帧调用一次，例如 `UpdateUI()` 方法）的高频代码路径。

4) **避免按值传递结构**

    与类不同，结构是值类型，将其直接传递给函数时，其内容将复制到新建的实例。 这种复制增加了 CPU 开销以及堆栈上的附加内存。 对于小型结构，这种影响通常可以忽略不计，因此是可接受的。 但是，对于要对每个帧重复调用的函数，以及采用大型结构的函数，如果可能，请修改函数定义以按引用传递。 [在此处了解详细信息](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>杂项

1) **物理学**

    a) 一般情况下，改善物理学的最简单方法是限制花费在物理学上的时间或每秒迭代次数。 当然，这会降低模拟准确度。 参阅 Unity 中的 [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)

    b) Unity 中的碰撞体类型具有广泛不同的性能特征。 下面从左到右按顺序列出了性能最高到性能最低的碰撞体。 最重要的是避免网格碰撞体，其开销要比基元碰撞体高出太多。

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    有关详细信息，请参阅 [Unity 物理学最佳做法](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)

2) **动画**

    通过禁用动画程序组件来禁用空闲动画（禁用游戏对象不会产生相同的效果）。 避免其动画程序循环将某个值设置为相同内容的设计模式。 此方法会产生相当大的开销，但对应用程序没有影响。 [在此处了解详细信息。](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **复杂算法**

    如果应用程序使用复杂算法，例如逆向运动、路径查找等，请努力找到更简单的方法，或调整其性能相关的设置

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU-GPU 性能建议

一般情况下，CPU-GPU 性能归根结底与提交到显卡的**绘制调用**相关。 为了改善性能，需要战略性地**减少**绘制调用，或**重新构建**绘制调用以获得最佳结果。 由于绘制调用本身是资源密集型的，减少此类调用可以减少所需的总体工作量。 此外，绘制调用之间的状态更改需要在图形驱动程序中执行高开销的验证和转换步骤，因此，重新构建应用程序的绘制调用来限制状态更改（例如 不同的材料等）可以大幅提高性能。

Unity 通过一篇详尽的文章概述并深入探讨了如何根据其平台批处理绘制调用。
- [Unity 绘制调用批处理](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>单通道实例化渲染

Unity 中的单通道实例化渲染使针对每只眼睛的绘制调用缩减为一个实例化绘制调用。 由于两个绘制调用之间的缓存内聚性，GPU 的性能也能得到一定的改善。

在 Unity 项目中启用此功能
1)  打开“播放器 XR 设置”（转到“编辑” > “项目设置” > “播放器” > “XR 设置”）     
2) 从“立体渲染方法”下拉菜单中选择“单通道实例化”（必须选中“支持虚拟现实”复选框）   

有关此渲染方法的详细信息，请阅读 Unity 的以下文章。
- [如何使用高级立体渲染最大化 AR 和 VR 的性能](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [单通道实例化](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 如果开发人员的现有自定义着色器不是针对实例化编写的，则单通道实例化渲染会发生一个常见问题。 启用此功能后，开发人员可能会注意到，某些 GameObject 只在一只眼睛中呈现。 这是因为，关联的自定义着色器没有与实例化相关的适当属性。
>
> 请参阅 Unity 文章 [HoloLens 的 单通道立体渲染](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)来了解如何解决此问题

#### <a name="static-batching"></a>静态批处理

Unity 能够批处理许多静态对象，以减少对 GPU 的绘制调用。 静态批处理适用于 Unity 中具有以下特征的大多数[渲染器](https://docs.unity3d.com/ScriptReference/Renderer.html)：**1) 共享相同的材料**；**2) 全部标记为 *Static*** （在 Unity 中选择一个对象，然后单击检查器右上角的复选框）。 标记为 *Static* 的 GameObject 无法在应用程序的整个运行时中移动。 因此，在几乎每个对象都需要进行定位、移动、缩放等操作的 HoloLens 上，可能很难利用静态批处理。对于沉浸式头戴显示设备，静态批处理可以大幅减少绘制调用，从而改善性能。

有关更多详细信息，请阅读 [Unity 中的绘制调用批处理](https://docs.unity3d.com/Manual/DrawCallBatching.html)下的“静态批处理”。 

#### <a name="dynamic-batching"></a>动态批处理

由于在 HoloLens 开发中将对象标记为 *Static* 会造成问题，动态批处理可能是弥补这项短缺功能的极佳手段。 当然，它也可用于沉浸式头戴显示设备。 不过，Unity 中的动态批处理可能很难启用，原因是 GameObject 必须 **a) 共享相同的材料**；**b) 符合其他很多条件**。

有关条件的完整列表，请阅读[Unity 中的绘制调用批处理](https://docs.unity3d.com/Manual/DrawCallBatching.html)下的“动态批处理”。  最常见的情况是，由于关联的网格数据不能超过 300 个顶点，因此 GameObject 无效，无法对其进行动态批处理。

#### <a name="other-techniques"></a>其他技术

仅当多个 GameObject 能够共享同一材料时，才会发生批处理。 通常，批处理受阻的原因是 GameObject 需要对其各自的材料使用独特的纹理。 开发人员往往将纹理合并成一个大纹理，此方法称为[纹理集合](https://en.wikipedia.org/wiki/Texture_atlas)。

此外，在可能且合理的情况下，他们倾向于将网格合并成一个 GameObject。 Unity 中的每个渲染器具有自身关联的绘制调用，而不是通过一个渲染器提交合并的网格。

>[!NOTE]
> 在运行时修改 Renderer.material 属性会创建材料的副本，因此可能会中断批处理。 使用 Renderer.sharedMaterial 可以修改各个 GameObject 的共享材料属性。

## <a name="gpu-performance-recommendations"></a>GPU 性能建议

详细了解[如何在 Unity 中优化图形渲染](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

### <a name="optimize-depth-buffer-sharing"></a>优化深度缓冲区共享

通常建议在“播放器 XR 设置”下启用“深度缓冲区共享”，以优化[全息影像稳定性](Hologram-stability.md)。   但是，在使用此设置的情况下启用基于深度的后期阶段重新投影时，建议选择 **16 位深度格式**而不是 **24 位深度格式**。 16 位深度缓冲区可以大幅减少与深度缓冲区流量相关的带宽（以及电量消耗）。 这可能会给节能和性能提升带来很大的好处。 但是，使用 *16 位深度格式*可能会造成两种负面影响。

**Z 冲突**

与 24 位相比，16 位的更低深度范围保真度更容易发生 [Z 冲突](https://en.wikipedia.org/wiki/Z-fighting)。 若要避免这种假象，请修改 [Unity 相机](https://docs.unity3d.com/Manual/class-Camera.html)的近距/远距剪裁平面，以采用更低的精度。 对于基于 HoloLens 的应用程序，50 米（而不是 Unity 的默认 1000 米）的远距剪裁平面通常可以消除任何 Z 冲突。

**已禁用模具缓冲区**

当 Unity 创建 [16 位深度的渲染纹理](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)时，不会创建模具缓冲区。 选择 24 位深度格式后，每个 Unity 文档将创建一个 24 位 Z 缓冲区和一个 [8 位模具缓冲区] (https://docs.unity3d.com/Manual/SL-Stencil.html) （如果 32 位在设备上适用，通常在 HoloLens 等设备上适用）。

### <a name="avoid-full-screen-effects"></a>避免全屏效果

全屏运行的技术可能会产生相当高的开销，因为它们的数量级是每帧数百万次操作。 因此，建议避免抗锯齿、开花等[后处理](https://docs.unity3d.com/Manual/PostProcessingOverview.html)效果。

### <a name="optimal-lighting-settings"></a>最佳照明设置

Unity 中的[实时全局照明](https://docs.unity3d.com/Manual/GIIntro.html)可以提供杰出的视觉效果，但涉及到开销很高的照明计算。 建议通过“窗口” > “渲染” > “照明设置”> 取消选中“实时全局照明”，为每个 Unity 场景文件禁用“实时全局照明”。    

此外，建议禁用所有阴影投射，因为这也会将高开销的 GPU 通道添加到 Unity 场景中。 可以按光源禁用阴影，但也可以通过“质量”设置对其进行整体控制。

转到“编辑” > “项目设置”，然后选择“质量”类别 > 为“UWP 平台”选择“低质量”。     还可以直接将“阴影”属性设置为“禁用阴影”。  

### <a name="reduce-poly-count"></a>减少多边形计数

通常可通过以下方式减少多边形计数
1) 从场景中删除对象
2) 抽离资产，以减少给定网格的多边形数目
3) 在应用程序中实施[详细级别 (LOD) 系统](https://docs.unity3d.com/Manual/LevelOfDetail.html)，以通过同一几何结构的较小多边形版本渲染远距离对象

### <a name="understanding-shaders-in-unity"></a>了解 Unity 中的着色器

若要大致比较着色器的性能，一种简单方法是识别每个着色器在运行时执行的平均操作数目。 可在 Unity 中轻松实现此目的。

1) 选择着色器资产或选择材料，然后在检查器窗口的右上角选择齿轮图标，然后选择“选择着色器” 

    ![在 Unity 中选择着色器](images/Select-shader-unity.png)
2) 选择着色器资产后，单击检查器窗口下的“编译并显示代码”按钮 

    ![在 Unity 中编译着色器代码](images/compile-shader-code-unity.PNG)

3) 编译后，查看结果中的统计信息部分，其中包含针对顶点和像素着色器（注意：像素着色器通常也称为段着色器）执行的不同操作数目

    ![Unity 标准着色器操作](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a>优化像素着色器

使用上述方法查看编译的统计信息结果时可以看到，[段着色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)执行的平均操作数目通常比[顶点着色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)更多。 段着色器（也称为像素着色器）是按屏幕输出中的像素执行的，而顶点着色器只是按屏幕上绘制的所有网格的每个顶点执行的。 

因此，段着色器不仅仅是指令数比顶点着色器更多（因为要执行所有照明计算），而且段着色器几乎总是针对较大数据集执行的。 例如，如果屏幕输出为 2,000 x 2,000 图像，则段着色器可能会执行 2,000*2,000 = 4,000,000 次。 如果渲染两只眼睛，此数字将会翻倍，因为有两个屏幕。 如果混合现实应用程序使用多个通道、全屏后处理效果或以相同的像素渲染多个网格，则此数字会大幅提高。 

因此，在段着色器中减少操作数目所带来的性能增益，通常远远好过在顶点着色器中进行优化。

#### <a name="unity-standard-shader-alternatives"></a>Unity 标准着色器替代技术

不要使用基于物理学的渲染 (PBR) 或其他优质着色器，而是寻求利用更高性能且更经济的着色器。 [混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供针对混合现实项目进行优化的 [MRTK 标准着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)。

与 Unity 标准着色器相比，Unity 还提供不发光、顶点发亮、漫射和其他简化的着色器选项。 有关更多详细信息，请参阅[内置着色器的用法和性能](https://docs.unity3d.com/Manual/shader-Performance.html)。

#### <a name="shader-preloading"></a>着色器预加载

使用着色器预加载和其他技巧优化[着色器加载时间](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)。  具体而言，着色器预加载意味着不会看到运行时着色器编译造成的任何帧聚结情况。

### <a name="limit-overdraw"></a>限制过度绘制

在 Unity 中，可以通过在“场景”视图的左上角切换[**绘制模式菜单**](https://docs.unity3d.com/Manual/ViewModes.html)并选择“过度绘制”，来显示其场景的过度绘制。  

一般情况下，在将对象发送到 GPU 之前提前剔除对象可以缓解过度绘制。 Unity 提供了有关为其引擎实现[遮挡剔除](https://docs.unity3d.com/Manual/OcclusionCulling.html)的详细信息。

## <a name="memory-recommendations"></a>内存建议

过多的内存分配和解除分配操作可能对全息应用程序产生负面影响，导致性能不稳定、帧冻结和其他不利行为。 在 Unity 中进行开发时，了解内存注意事项特别重要，因为内存管理由垃圾回收器进行控制。

#### <a name="garbage-collection"></a>垃圾回收

在执行期间激活垃圾回收器 (GC) 来分析不再处于范围内的对象时，如果需要释放对象的内存以便可供重复使用，则全息应用会将处理计算时间损失在 GC 上。 连续的分配和解除分配通常需要垃圾回收器更频繁地运行，因此会损害性能和用户体验。

Unity 在一个很好的网页中详细说明了垃圾回收器的工作原理，并提供了有关如何为内存管理编写更高效代码的提示。
- [优化 Unity 游戏中的垃圾回收](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

导致过度垃圾回收的最常见原因之一是在 Unity 开发中不缓存对组件和类的引用。 应在运行 Start() 或 Awake() 期间捕获所有引用，并在以后运行 Update() 或 LateUpdate() 等函数期间重复使用这些引用。

其他快速提示：
- 在运行时使用 [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# 类动态生成复杂字符串
- 删除不再需要的 Debug.Log() 调用，因为它们仍会在应用的所有生成版本中执行
- 如果全息应用通常需要大量的内存，请考虑在加载阶段（例如，在演示加载或过渡屏幕时）调用 [ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)

#### <a name="object-pooling"></a>对象池

对象池是一种热门技术，可以降低对象连续分配和解除分配所造成的开销。 此技术是通过以下方式实现的：分配一个由相同对象构成的较大池并重复使用此池中非活动的可用实例，而不是在各个时间内不断生成和销毁对象。 对象池非常适合应用中生存期可变的可重用组件。

- [Unity 中的对象池教程](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>启动性能

应考虑使用较小的场景启动应用，然后使用 *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 加载场景的剩余部分。 这样，应用就可以尽快进入交互状态。 请注意，在激活新场景时，可能会出现较大的 CPU 峰值，并且渲染的任何内容可能会出现断连或聚结。 解决此问题的方法之一是，在所要加载的场景中将 AsyncOperation.allowSceneActivation 属性设置为“false”，等待场景加载完成，将屏幕清理为黑屏，然后将此属性重新设置为“true”以完成场景激活。

请记住，在加载启动场景时，会向用户显示全息初始屏幕。

## <a name="see-also"></a>另请参阅
- [优化 Unity 游戏中的图形渲染](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [优化 Unity 游戏中的垃圾回收](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [物理学最佳做法 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [优化脚本 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
