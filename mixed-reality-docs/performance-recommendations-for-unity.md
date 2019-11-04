---
title: Unity 性能建议
description: 用于提高混合现实应用性能的 Unity 特定的提示。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 图形，cpu，gpu，呈现，垃圾回收，hololens
ms.openlocfilehash: 724ec24408e70360fda07c59a4ca2ffc30b49c1f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438126"
---
# <a name="performance-recommendations-for-unity"></a>Unity 性能建议

本文基于[混合现实的性能建议](understanding-performance-for-mixed-reality.md)中所述的讨论，但重点介绍特定于 Unity 引擎环境的知识。

同时，强烈建议开发人员查看[Unity 项目的推荐环境设置](Recommended-settings-for-unity.md)。 本文提供了一些内容，其中包含一些最重要的场景配置，用于构建性能混合的现实应用。 下面突出显示了其中一些推荐的设置。

## <a name="how-to-profile-with-unity"></a>如何用 Unity 进行分析

Unity 提供了 **[Unity 探查器](https://docs.unity3d.com/Manual/Profiler.html)** ，这是一个很好的资源，可为你的特定应用收集宝贵的性能见解。 尽管可以在编辑器中运行探查器，但这些度量值并不表示真正的运行时环境，因此应该谨慎使用。 建议在设备上运行时远程分析应用程序，以获得最准确且可操作的见解。 此外，Unity 的[框架调试程序](https://docs.unity3d.com/Manual/FrameDebugger.html)也是一个非常强大的工具，可供使用。

Unity 为以下方面提供了强大的文档：
1) 如何[远程将 Unity 探查器连接到 UWP 应用程序](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) 如何[通过 Unity 探查器有效地诊断性能问题](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> 当 Unity 探查器已连接并在添加 GPU 探查器后（请参阅右上角的 "*添加探查器*"），可以在探查器中间分别查看在 CPU 上花费了多少时间 & GPU。 这允许开发人员在其应用程序是 CPU 或 GPU 限制的情况下获得快速近似值。
>
> ![Unity CPU 与 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU 性能建议

以下内容介绍了更深入的性能做法，尤其针对 Unity & C#开发。

#### <a name="cache-references"></a>缓存引用

最佳做法是在初始化时缓存对所有相关组件和 Gameobject 的引用。 这是因为重复函数调用（如 *[GetComponent\<t > （）](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 相对于存储指针所需的内存成本要高得多。 这也适用于经常使用的[相机。](https://docs.unity3d.com/ScriptReference/Camera-main.html) *摄影机*实际上只是使用 *[FindGameObjectsWithTag （）](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* ，低廉在其下使用 *"MainCamera"* 标记在场景图中搜索相机对象。

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
> 避免 GetComponent （字符串） <br/>
> 使用 *[GetComponent （）](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 时，有少量的不同重载。 应始终使用基于类型的实现，而不是基于字符串的搜索重载，这一点非常重要。 在场景中按字符串搜索比按类型搜索要大得多。 <br/>
> 良好Component GetComponent （类型类型） <br/>
> 良好T GetComponent\<T > （） <br/>
> Dfx组件 GetComponent （字符串） > <br/>

#### <a name="avoid-expensive-operations"></a>避免成本高昂的操作

1) **避免使用[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    尽管 LINQ 可以非常简洁、易于读写，但它通常需要更多的计算和更多的内存分配，而不是手动写入算法。

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **公共 Unity Api**

    某些 Unity Api 虽然有用，但执行起来可能非常昂贵。 其中的大多数都涉及在整个场景图中搜索 Gameobject 的一些匹配列表。 通常可以通过缓存引用或实现 Gameobject 中的管理器组件来避免这些操作，以跟踪运行时的引用。

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> 应该消除 *[SendMessage （）](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 和 *[BroadcastMessage （）](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 。 这些函数的顺序可能比直接函数调用慢1000倍。

3) **注意装箱**

    [装箱](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)是C#语言和运行时的核心概念。 它是将值类型化变量（如 char、int、bool 等）包装到引用类型变量的过程。 当值类型的变量为 "装箱" 时，它将包装在存储在托管堆上的 System.object 内。 因此，内存将被分配，最终当必须由垃圾回收器处理时，必须处理内存。 这些分配和释放会产生性能开销，在许多情况下都是不必要的，或者可以轻松地将其替换为开销较低的替代项。

    开发中最常见的装箱形式之一是使用[可以为 null 的值类型](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)。 当操作可能无法尝试获取值时，通常需要能够在函数中返回值类型为 null 的情况。 此方法可能存在的问题是，分配现在发生在堆上，因此需要在以后对其进行垃圾回收。

    **中的装箱示例C#**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **通过可为 null 的值类型进行装箱的示例**

    此代码演示一个虚拟粒子类，该类可以在 Unity 项目中创建。 对 `TryGetSpeed()` 的调用将导致堆上的对象分配，需要在以后的某个时间点对该对象进行垃圾回收。 此示例尤其有问题，因为场景中可能有1000个或更多粒子，每个粒子都要求提供当前速度。 因此，将分配1000个对象，因而每个帧都将释放，这会大大降低性能。 重新编写函数以返回一个负值（例如-1），以指示失败将避免此问题并使内存在堆栈上。

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

任何重复的 Unity 回调函数（即 更新），则应仔细编写每秒和/或帧的多次执行。 此处的任何昂贵操作都将对性能产生巨大的一致性影响。

1) **空回调函数**

    尽管下面的代码在应用程序中可能看似不合法，尤其是由于每个 Unity 脚本都是通过此代码块自动初始化的，因此这些空回调实际上可能会非常昂贵。 Unity 在 UnityEngine 代码和应用程序代码之间的非托管/托管代码边界之间来回操作。 即使没有要执行的操作，通过此桥的上下文切换也相当昂贵。 如果你的应用程序的 Gameobject 与具有空的重复 Unity 回调的组件具有100个，这会变得非常有问题。

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update （）是此性能问题的最常见表现形式，但其他重复 Unity 回调（如以下）可能会像下面那样糟糕： FixedUpdate （）、Behaviour （）、OnPostRender、OnPreRender （）、OnRenderImage （）等。 

2) **针对每个帧运行一次的操作**

    以下 Unity Api 是许多全息应用的常见操作。 尽管并非总是可行，但这些函数的结果通常也可以计算一次，并且会在应用程序中为给定帧重新利用结果。

    答：使用专用的单独类或服务，可以将您的注视 Raycast 处理到场景中，然后在所有其他场景组件中重复使用此结果，而不是每组件. 当然，某些应用程序可能需要来自不同来源的 raycasts 或不同的[LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)。

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b）通过在 Start （）或唤醒（）中[缓存引用](#cache-references)来避免重复的 Unity 回调（如 Update （））中的 GetComponent （）操作

        UnityEngine.Object.GetComponent()

    c）最好在初始化时实例化所有对象，并在应用程序运行时使用[对象池](#object-pooling)来回收和重复使用 Gameobject，这是一种很好的做法。

        UnityEngine.Object.Instantiate()

3) **避免接口和虚拟构造**

    与使用直接构造或直接函数调用相比，通过接口调用函数调用和直接对象或调用虚函数通常会更昂贵。 如果不需要虚拟函数或接口，则应将其删除。 不过，如果利用它们来简化开发协作、代码可读性和代码可维护性，通常值得权衡这些方法的性能。

    通常，建议不要将字段和函数标记为虚拟，除非明确要求覆盖此成员。 应特别注意每个帧调用了多次（甚至每帧一次，例如 `UpdateUI()` 方法）的高频代码路径。

4) **避免通过值传递结构**

    与类不同的是，结构是值类型，并在直接传递到函数时，将其内容复制到新创建的实例。 此副本增加了 CPU 开销以及堆栈上的额外内存。 对于小型结构，效果通常非常小，因此是可接受的。 但是，对于每个帧以及采用大型结构的函数重复调用的函数，如果可能，请修改函数定义以通过引用传递。 [在此处了解详细信息](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>其他

1) **物理**

    a）一般来说，提高物理学的最简单方法是限制在物理学上花费的时间量或每秒迭代的次数。 当然，这会降低模拟准确性。 请参阅 Unity 中的[TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)

    b） Unity 中的 colliders 类型具有广泛不同的性能特征。 下面的顺序列出了从左到右的最 colliders 高性能 colliders 的最高性能。 最重要的是避免网格 Colliders，这比基元 Colliders 大得多。

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    有关详细信息，请参阅[Unity 物理学最佳实践](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)

2) **效果**

    禁用 Animator 组件禁用空闲动画（禁用游戏对象不会产生相同的效果）。 避免 animator 所在的设计模式将值设置为相同的值。 此方法会产生相当大的开销，对应用程序没有影响。 [在此处了解详细信息。](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **复杂算法**

    如果你的应用程序使用的是复杂的算法，如反向运动、路径查找等，查找更简单的方法或调整相关设置的性能

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU 到 GPU 性能建议

通常情况下，CPU 到 GPU 的性能会下降到提交到图形卡的**绘图调用**。 若要提高性能，需要以战略**a 的**方式绘制调用，或将其作为最佳结果**重构**。 由于绘图调用本身会消耗大量资源，因此减少它们会减少所需的全部工作。 此外，在绘图调用之间进行的状态更改需要在图形驱动程序中执行昂贵的验证和翻译步骤，因此，重新构建应用程序的绘图调用以限制状态更改（即 不同的资料等）可以提高性能。

Unity 提供了一个很好的文章，为其平台的批处理绘图调用提供了概述和深入。
- [Unity 绘图调用批处理](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>单次传递实例呈现

Unity 中的单个 Pass 实例呈现允许每个眼睛的绘图调用缩小到一个实例绘图调用。 由于两次绘图调用之间的缓存一致性，因此也会对 GPU 进行一些性能改进。

在 Unity 项目中启用此功能
1)  打开**播放机 XR 设置**（ > **Player** > "**设置**" "**编辑**" > **项目设置**
2) 从 "**立体声呈现方法**" 下拉菜单中选择 "**单一传递实例**" （必须选中 "**支持虚拟现实**" 复选框）

有关此呈现方法的详细信息，请阅读有关 Unity 的以下文章。
- [如何通过高级立体声呈现最大化 AR 和 VR 性能](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [单步实例](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 如果开发人员已有未为实例化编写的现有自定义着色器，则会出现单一传递实例呈现的一个常见问题。 启用此功能后，开发人员可能会注意到某些 Gameobject 只会在一眼中呈现。 这是因为关联的自定义着色器没有用于实例化的适当属性。
>
> 有关如何解决此问题的详细说明，请参阅针对基于 Unity 的[HoloLens 的单一传递立体声呈现](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)

#### <a name="static-batching"></a>静态批处理

Unity 能够批处理多个静态对象，以减少对 GPU 的调用。 静态批处理适用于 Unity 中的大多数[呈现](https://docs.unity3d.com/ScriptReference/Renderer.html)器对象**1）共享相同的材料**， **2）全部标记为*静态*** （选择 Unity 中的对象，然后单击检查器右上方的复选框）。 不能在应用程序的运行时中移动标记为*静态*的 gameobject。 因此，静态批处理可能难以在 HoloLens 上利用，几乎每个对象都需要放置、移动、缩放等。对于沉浸式耳机，静态批处理可以显著减少绘图调用，从而提高性能。

有关更多详细信息，请参阅[Unity 中的绘图调用批处理中](https://docs.unity3d.com/Manual/DrawCallBatching.html)的*静态批处理*。

#### <a name="dynamic-batching"></a>动态批处理

由于将对象标记为适用于 HoloLens 开发的*静态*对象是有问题的，因此动态批处理可以很好地用于补偿此缺少的功能。 当然，它也可用于沉浸式耳机。 如果启用 Unity 中的动态批处理，则可能会很难，因为 Gameobject 必须**是）共享相同的材料**和**b），以满足较长的其他标准列表**。

有关完整列表，请参阅在[Unity 中的绘图调用批处理中](https://docs.unity3d.com/Manual/DrawCallBatching.html)的*动态批处理*。 最常见的情况是，Gameobject 因为关联的网格数据不能超过300个顶点而变为无效。

#### <a name="other-techniques"></a>其他技术

仅当多个 Gameobject 可以共享同一材料时才会进行批处理。 通常，这将被阻止 Gameobject 对其各自的材料具有独特的纹理。 将纹理组合到一个大纹理（一种称为[纹理 Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)的方法）是很常见的。

此外，更好的做法是，尽可能将网格合并到一个 GameObject 中。 Unity 中的每个呈现器都将具有关联的绘图调用，而不是在一个呈现器下提交组合网格。

>[!NOTE]
> 修改呈现器的属性时，在运行时将创建材料的副本，因此可能会破坏批处理。 使用 sharedMaterial 可跨 Gameobject 修改共享的材料属性。

## <a name="gpu-performance-recommendations"></a>GPU 性能建议

了解有关[优化 Unity 中的图形呈现的](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)详细信息

### <a name="optimize-depth-buffer-sharing"></a>优化深度缓冲区共享

通常建议在**播放机 XR 设置**下启用**深度缓冲区共享**以优化[全息影像稳定性](Hologram-stability.md)。 但是，在使用此设置启用基于深度的后期 reprojection 时，建议选择**16 位深度格式**而不是**24 位深度格式**。 16位深度缓冲区会大幅降低与深度缓冲区通信关联的带宽（以及与电源相关的能力）。 这可以是同时降低电源和性能的巨大优势。 但是，通过使用*16 位深度格式*可以产生两个可能的负面结果。

**Z-反击**

降低深度范围保真使比24位更有可能出现[z 反击](https://en.wikipedia.org/wiki/Z-fighting)。 若要避免这些项目，请修改[Unity 相机](https://docs.unity3d.com/Manual/class-Camera.html)的 "近处/远处" 剪辑平面以降低精度。 对于基于 HoloLens 的应用程序，50m （而不是 Unity 的默认1000m）的 far 剪裁平面通常可以消除任何 z 反击。

**禁用的模具缓冲区**

当 Unity 创建[具有16位深度的着色纹理](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)时，不会创建任何模具缓冲区。 选择24位深度格式后，每个 Unity 文档将创建一个24位 z 缓冲区和一个[8 位的模具缓冲区](https://docs.unity3d.com/Manual/SL-Stencil.html)（如果32位适用于通常情况下的设备，如 HoloLens）。

### <a name="avoid-full-screen-effects"></a>避免全屏效果

在全屏幕上操作的方法可能相当昂贵，因为它们的数量级顺序是每个帧的数百万个操作。 因此，建议避免使用[后期处理效果](https://docs.unity3d.com/Manual/PostProcessingOverview.html)，如抗锯齿、布隆等。

### <a name="optimal-lighting-settings"></a>最佳照明设置

Unity 中的[实时全局照明](https://docs.unity3d.com/Manual/GIIntro.html)可提供数量的视觉效果，但涉及到非常昂贵的照明计算。 建议通过**窗口** > **呈现**为每个 Unity 场景文件禁用实时全局照明 > **照明设置**> 取消选中 "**实时全局照明**"。

此外，建议禁用所有阴影转换，因为这也会将昂贵的 GPU 传递添加到 Unity 场景。 可以按光禁用阴影，但也可以通过质量设置对其进行控制整体。

**编辑** > **项目设置**，然后选择 "**质量**" 类别 > 为 UWP 平台选择**低质量**。 还可以仅设置**shadows**属性来**禁用阴影**。

### <a name="reduce-poly-count"></a>减少 poly 计数

多边形计数通常通过
1) 从场景中删除对象
2) 降低给定网格的多边形数的资产 decimation
3) 在应用程序中实现[级别的详细信息（LOD）系统](https://docs.unity3d.com/Manual/LevelOfDetail.html)，该系统将呈现远离相同几何图形的较小多边形版本的对象

### <a name="understanding-shaders-in-unity"></a>了解 Unity 中的着色器

比较性能着色器的简单近似值是确定每个运行时执行的平均操作数。 可在 Unity 中轻松完成此操作。

1) 选择着色器资产或选择材料，然后在检查器窗口的右上角选择齿轮图标，然后选择 **"选择着色器"**

    ![选择 Unity 中的着色器](images/Select-shader-unity.png)
2) 选择着色器资产后，单击 "检查器" 窗口下的 **"编译并显示代码"** 按钮

    ![在 Unity 中编译着色器代码](images/compile-shader-code-unity.PNG)

3) 编译完成后，查找结果中的 "统计信息" 部分，其中包含用于顶点着色器和像素着色器的不同操作（注意：像素着色器通常也称为片段着色器）

    ![Unity 标准着色器操作](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a>优化像素着色器

使用上述方法查看编译的统计信息结果，[片段着色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)通常执行的操作比平均[顶点着色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)要多。 片段着色器（也称为像素着色器）在屏幕输出上按像素执行，而顶点着色器仅对绘制到屏幕的所有网格的每个顶点执行。 

因此，与顶点着色器相比，不仅仅是由于所有照明计算，片段着色器都有更多的说明，碎片着色器几乎总是在较大的数据集上执行。 例如，如果屏幕输出为 2k x 2k，则片段着色器可以执行 2000 * 2000 = 4000000 次。 如果呈现两个眼睛，此数字会加倍，因为有两个屏幕。 如果混合现实应用程序具有多个传递、全屏后处理效果或将多个网格呈现到同一个像素，则此数字会大幅增加。 

因此，在片段着色器中减少操作的数量通常可以比顶点着色器中的优化更好地提高性能。

#### <a name="unity-standard-shader-alternatives"></a>Unity 标准着色器替代项

请不要使用基于物理的渲染（.PBR）或其他高质量的着色器，而是了解如何利用更高性能和更便宜的着色器。 [混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供了已针对混合现实项目进行优化的[MRTK 标准着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)。

与 Unity 标准着色器相比，Unity 还提供了 unlit、顶点发亮、漫射以及其他简化的着色器选项。 有关更多详细信息，请参阅[内置着色器的使用情况和性能](https://docs.unity3d.com/Manual/shader-Performance.html)。

#### <a name="shader-preloading"></a>着色器预加载

使用*着色器预加载*和其他技巧优化[着色器的加载时间](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)。 特别是，着色器预加载意味着你不会看到任何 hitches，因为运行时着色器编译。

### <a name="limit-overdraw"></a>限制过度绘制

在 Unity 中，可以通过在**场景视图**的左上角切换 "[**绘图模式" 菜单**](https://docs.unity3d.com/Manual/ViewModes.html)并选择 "**过度绘制**"，为其场景显示过度绘制。

通常，在将对象发送到 GPU 之前提前剔除对象，可减轻过度绘制。 Unity 提供了有关为其引擎实现[封闭剔除](https://docs.unity3d.com/Manual/OcclusionCulling.html)的详细信息。

## <a name="memory-recommendations"></a>内存建议

内存分配过多 & 释放操作可能对全息应用程序产生不利影响，从而导致性能不一致、冻结帧和其他不利行为。 在 Unity 中进行开发时，了解内存的注意事项尤其重要，因为内存管理由垃圾回收器控制。

#### <a name="garbage-collection"></a>垃圾回收

激活 GC 时，全息应用会将计算时间松散地处理到垃圾回收器（GC），以分析在执行期间不再处于范围内的对象，从而使其可供重复使用。 常数分配和取消分配通常需要垃圾回收器才能更频繁地运行，从而影响性能和用户体验。

Unity 提供了一个很好的页面，其中详细说明了垃圾回收器的工作方式，以及如何编写更高效的代码来处理内存管理。
- [优化 Unity 游戏中的垃圾回收](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

导致过多垃圾回收的最常见做法之一是不会缓存对 Unity 开发中的组件和类的引用。 任何引用都应在开始（）或唤醒（）期间捕获，并在后续函数（如 Update （）或 Behaviour （））中重新使用。

其他快速提示：
- 使用[StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C#类在运行时动态生成复杂字符串
- 当不再需要 Log （）时，请将其删除，因为它们仍在应用的所有内部版本中执行
- 如果您的全息应用程序通常需要大量内存，请考虑在加载阶段（例如，在呈现加载或转换屏幕时[ _**）调用 system.web**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) 。

#### <a name="object-pooling"></a>对象池

对象池是一种常用技术，可降低对象 & 释放的持续分配成本。 这是通过以下方式实现的：分配一个较大的相同对象池，并重新使用此池中的非活动可用实例，而不是随着时间推移不断地生成和销毁对象。 对象池非常适合在应用过程中具有可变生存期的重复使用的组件。

- [Unity 中的对象池教程](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>启动性能

你应考虑使用较小的场景启动你的应用程序，然后使用 *[SceneManager](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 加载场景的其余部分。 这允许你的应用程序尽可能快地进入交互状态。 请注意，当新场景正在激活并且任何呈现的内容可能断断续续或不便时，可能会出现较大的 CPU 峰值。 解决这种情况的一种方法是，在要加载的场景上将 AsyncOperation. allowSceneActivation 属性设置为 false，等待场景加载，将屏幕清除为黑色，然后将其重新设置为 true 以完成场景激活。

请记住，当启动场景正在加载时，将向用户显示全息的初始屏幕。

## <a name="see-also"></a>另请参阅
- [优化 Unity 游戏中的图形呈现](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [优化 Unity 游戏中的垃圾回收](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [物理学最佳实践 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [优化脚本 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
