---
title: 针对 Unity 的性能建议
description: 有关提高混合现实应用性能的 Unity 特定提示。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 图形, cpu, gpu, 渲染, 垃圾回收, hololens
ms.localizationpriority: high
ms.openlocfilehash: 18691ab7993b2802268d3c4ce05532dfa5bd1723
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160013"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="ced3f-104">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="ced3f-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="ced3f-105">本文是在[针对混合现实的性能建议](understanding-performance-for-mixed-reality.md)中所述内容的基础上编写的，但重点介绍特定于 Unity 引擎环境的知识。</span><span class="sxs-lookup"><span data-stu-id="ced3f-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unity engine environment.</span></span>

## <a name="use-recommended-unity-project-settings"></a><span data-ttu-id="ced3f-106">使用建议的 Unity 项目设置</span><span class="sxs-lookup"><span data-stu-id="ced3f-106">Use recommended Unity project settings</span></span>

<span data-ttu-id="ced3f-107">在 Unity 中优化混合现实应用的性能时，最重要的第一步是确保使用[建议用于 Unity 的环境设置](recommended-settings-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="ced3f-107">The most important first step when optimizing performance of mixed reality apps in Unity is to be sure you are using the [recommended environment settings for Unity](recommended-settings-for-unity.md).</span></span> <span data-ttu-id="ced3f-108">该文中的内容涉及到一些对于生成高性能混合现实应用至关重要的场景配置。</span><span class="sxs-lookup"><span data-stu-id="ced3f-108">That article contains content with some of the most important scene configurations for building performant Mixed Reality apps.</span></span> <span data-ttu-id="ced3f-109">本文也强调了其中建议的一些设置。</span><span class="sxs-lookup"><span data-stu-id="ced3f-109">Some of these recommended settings are highlighted below, as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="ced3f-110">如何使用 Unity 进行探查</span><span class="sxs-lookup"><span data-stu-id="ced3f-110">How to profile with Unity</span></span>

<span data-ttu-id="ced3f-111">Unity 提供内置的 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** ，它是一个极佳的资源，可以收集特定应用的重要性能见解。</span><span class="sxs-lookup"><span data-stu-id="ced3f-111">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in, which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="ced3f-112">尽管用户可以在编辑器中运行该探查器，但这些指标并不代表真正的运行时环境，因此应该慎用其结果。</span><span class="sxs-lookup"><span data-stu-id="ced3f-112">Although one can run the profiler in-editor, these metrics do not represent the true runtime environment and thus, results from this should be used cautiously.</span></span> <span data-ttu-id="ced3f-113">建议在设备上运行应用程序时远程对其进行探查，以获得最准确且可对其采取措施的见解。</span><span class="sxs-lookup"><span data-stu-id="ced3f-113">It is recommended to remotely profile your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="ced3f-114">此外，Unity 的 [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) 也是一个非常强大的见解工具。</span><span class="sxs-lookup"><span data-stu-id="ced3f-114">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) is also a very powerful and insight tool to utilize.</span></span>

<span data-ttu-id="ced3f-115">Unity 提供了以下方面的详尽文档：</span><span class="sxs-lookup"><span data-stu-id="ced3f-115">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="ced3f-116">如何[将 Unity Profiler 远程连接到 UWP 应用程序](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span><span class="sxs-lookup"><span data-stu-id="ced3f-116">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="ced3f-117">如何有效[使用 Unity Profiler 诊断性能问题](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span><span class="sxs-lookup"><span data-stu-id="ced3f-117">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="ced3f-118">在连接 Unity Profiler 并添加 GPU 探查器后（查看右上角的“添加探查器”），可以在探查器的中间分别查看花费在 CPU 和 GPU 上的时间。 </span><span class="sxs-lookup"><span data-stu-id="ced3f-118">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="ced3f-119">这样，开发人员很快就能大致了解其应用程序是受 CPU 还是 GPU 的约束。</span><span class="sxs-lookup"><span data-stu-id="ced3f-119">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU 与 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="ced3f-121">CPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="ced3f-121">CPU performance recommendations</span></span>

<span data-ttu-id="ced3f-122">以下内容涵盖更深入的性能做法，特别适合在 Unity 和 C# 开发中采用。</span><span class="sxs-lookup"><span data-stu-id="ced3f-122">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="ced3f-123">缓存引用</span><span class="sxs-lookup"><span data-stu-id="ced3f-123">Cache references</span></span>

<span data-ttu-id="ced3f-124">最佳做法是在初始化时缓存对所有相关组件和 GameObject 的引用。</span><span class="sxs-lookup"><span data-stu-id="ced3f-124">It is best practice to cache references to all relevant components and GameObjects at initialization.</span></span> <span data-ttu-id="ced3f-125">这是因为，与存储指针所产生的内存开销相比，重复 *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 之类的函数调用所造成的开销要高得多。</span><span class="sxs-lookup"><span data-stu-id="ced3f-125">This is because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* are significantly more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="ced3f-126">这同样适用于极度频繁使用的 [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)。</span><span class="sxs-lookup"><span data-stu-id="ced3f-126">This also applies to to the very regularly used [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).</span></span> <span data-ttu-id="ced3f-127">*Camera.main* 实际上在幕后只是使用 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* ，但却以很高的开销在场景图中搜索具有 *“MainCamera”* 标记的相机对象。</span><span class="sxs-lookup"><span data-stu-id="ced3f-127">*Camera.main* actually just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath, which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

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
> <span data-ttu-id="ced3f-128">避免 GetComponent(string)</span><span class="sxs-lookup"><span data-stu-id="ced3f-128">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="ced3f-129">使用 *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 时，会产生少量不同的重载。</span><span class="sxs-lookup"><span data-stu-id="ced3f-129">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="ced3f-130">必须始终使用基于类型的实现，切勿使用基于字符串的搜索重载。</span><span class="sxs-lookup"><span data-stu-id="ced3f-130">It is important to always use the Type-based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="ced3f-131">在场景中按字符串进行搜索，比按类型进行搜索的开销要高得多。</span><span class="sxs-lookup"><span data-stu-id="ced3f-131">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="ced3f-132">（正确）Component GetComponent(Type type)</span><span class="sxs-lookup"><span data-stu-id="ced3f-132">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="ced3f-133">（正确）T GetComponent\<T>()</span><span class="sxs-lookup"><span data-stu-id="ced3f-133">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="ced3f-134">（错误）Component GetComponent(string)></span><span class="sxs-lookup"><span data-stu-id="ced3f-134">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="ced3f-135">避免高开销的操作</span><span class="sxs-lookup"><span data-stu-id="ced3f-135">Avoid expensive operations</span></span>

1) <span data-ttu-id="ced3f-136">**避免使用 [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span><span class="sxs-lookup"><span data-stu-id="ced3f-136">**Avoid use of [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="ced3f-137">尽管 LINQ 非常简洁且易于读写，但与手动写出算法相比，它所需的计算资源要多得多，尤其是内存分配。</span><span class="sxs-lookup"><span data-stu-id="ced3f-137">Although LINQ can be very clean and easy to read and write, it generally requires much more computation and particularly more memory allocation than writing the algorithm out manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="ced3f-138">**通用 Unity API**</span><span class="sxs-lookup"><span data-stu-id="ced3f-138">**Common Unity APIs**</span></span>

    <span data-ttu-id="ced3f-139">某些 Unity API 虽然很有用，但其执行开销可能极高。</span><span class="sxs-lookup"><span data-stu-id="ced3f-139">Certain Unity APIs, although useful, can be very expensive to execute.</span></span> <span data-ttu-id="ced3f-140">其中的大部分 API 都涉及到在整个场景图中搜索 GameObject 的匹配列表。</span><span class="sxs-lookup"><span data-stu-id="ced3f-140">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="ced3f-141">一般情况下，若要避免这些操作，可以缓存引用，或者实现相关 GameObject 的管理器组件，以在运行时跟踪引用。</span><span class="sxs-lookup"><span data-stu-id="ced3f-141">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects in question to track the references at runtime.</span></span>

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> <span data-ttu-id="ced3f-142">应该消除 *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 和 *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 的所有开销。</span><span class="sxs-lookup"><span data-stu-id="ced3f-142">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="ced3f-143">与直接函数调用相比，这些函数可能要慢上若干千倍。</span><span class="sxs-lookup"><span data-stu-id="ced3f-143">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="ced3f-144">**注意装箱**</span><span class="sxs-lookup"><span data-stu-id="ced3f-144">**Beware of boxing**</span></span>

    <span data-ttu-id="ced3f-145">[装箱](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)是 C# 语言和运行时的核心概念。</span><span class="sxs-lookup"><span data-stu-id="ced3f-145">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="ced3f-146">它是将值类型化变量（例如 char、int、bool 等）包装到引用类型化变量中的过程。</span><span class="sxs-lookup"><span data-stu-id="ced3f-146">It is the process of wrapping value-typed variables such as char, int, bool, etc. into reference-typed variables.</span></span> <span data-ttu-id="ced3f-147">将值类型化变量“装箱”后，该变量将包装在 System.Object 内，后者存储在托管堆上。</span><span class="sxs-lookup"><span data-stu-id="ced3f-147">When a value-typed variable is "boxed", it is wrapped inside of a System.Object which is stored on the managed heap.</span></span> <span data-ttu-id="ced3f-148">因此，需要分配内存，并在最终释放内存后，由垃圾回收器处理内存。</span><span class="sxs-lookup"><span data-stu-id="ced3f-148">Thus, memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="ced3f-149">这种分配和解除分配会损害性能，且在许多情况下是不必要的，或者可以由开销更低的替代做法轻松取代。</span><span class="sxs-lookup"><span data-stu-id="ced3f-149">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

    <span data-ttu-id="ced3f-150">开发中最常见的装箱形式之一是使用[可为 null 值类型](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)。</span><span class="sxs-lookup"><span data-stu-id="ced3f-150">One of the most common forms of boxing in development is the use of [nullable value types](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/).</span></span> <span data-ttu-id="ced3f-151">开发人员经常希望能够在函数中为值类型返回 null，尤其是操作在尝试获取该值可能失败的情况下。</span><span class="sxs-lookup"><span data-stu-id="ced3f-151">It is common to want to be able to return null for a value type in a function, especially when the operation may fail trying to get the value.</span></span> <span data-ttu-id="ced3f-152">此方法的潜在问题是，现在分配在堆上发生，因此以后需要进行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="ced3f-152">The potential problem with this approach is that allocation now occurs on the heap and consequently needs to be garbage collected later.</span></span>

    <span data-ttu-id="ced3f-153">**C# 中的装箱示例**</span><span class="sxs-lookup"><span data-stu-id="ced3f-153">**Example of boxing in C#**</span></span>

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    <span data-ttu-id="ced3f-154">**通过可为 null 值类型进行装箱出现问题的示例**</span><span class="sxs-lookup"><span data-stu-id="ced3f-154">**Example of problematic boxing via nullable value types**</span></span>

    <span data-ttu-id="ced3f-155">此代码演示一个可在 Unity 项目中创建的虚构粒子类。</span><span class="sxs-lookup"><span data-stu-id="ced3f-155">This code demonstrates a dummy particle class that one may create in a Unity project.</span></span> <span data-ttu-id="ced3f-156">对 `TryGetSpeed()` 的调用将导致在堆上分配对象，因此需要在以后的某个时间点进行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="ced3f-156">A call to `TryGetSpeed()` will cause object allocation on the heap which will need to be garbage collected at a later point in time.</span></span> <span data-ttu-id="ced3f-157">在此示例中之所以会出现特定的问题，是因为场景中可能有 1000 个甚至更多的粒子，而函数需要查询每个粒子的当前速度。</span><span class="sxs-lookup"><span data-stu-id="ced3f-157">This example is particularly problematic as there may be 1000+ or many more particles in a scene, each being asked for their current speed.</span></span> <span data-ttu-id="ced3f-158">这样，就要分配数千个对象，因而要解除分配每个帧，这会极大地降低性能。</span><span class="sxs-lookup"><span data-stu-id="ced3f-158">Thus, 1000's of objects would be allocated and consequently de-allocated every frame, which would greatly diminish performance.</span></span> <span data-ttu-id="ced3f-159">重新编写函数以返回一个负值（例如 -1）来指示失败可以避免此问题，并在堆栈上保留内存。</span><span class="sxs-lookup"><span data-stu-id="ced3f-159">Re-writing the function to return a negative value such as -1 to indicate a failure would avoid this issue and keep memory on the stack.</span></span>

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

#### <a name="repeating-code-paths"></a><span data-ttu-id="ced3f-160">重复代码路径</span><span class="sxs-lookup"><span data-stu-id="ced3f-160">Repeating code paths</span></span>

<span data-ttu-id="ced3f-161">应该精心编写每秒要执行多次的任何</span><span class="sxs-lookup"><span data-stu-id="ced3f-161">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="ced3f-162">重复性 Unity 回调函数（例如 Update）和/或帧。</span><span class="sxs-lookup"><span data-stu-id="ced3f-162">Update) that are executed many times per second and/or frame should be written very carefully.</span></span> <span data-ttu-id="ced3f-163">此处发生的任何高开销操作都会对性能持续造成巨大影响。</span><span class="sxs-lookup"><span data-stu-id="ced3f-163">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="ced3f-164">**空回调函数**</span><span class="sxs-lookup"><span data-stu-id="ced3f-164">**Empty callback functions**</span></span>

    <span data-ttu-id="ced3f-165">在应用程序中保留以下代码看似没有妨碍，尤其是因为每个 Unity 脚本都要通过此代码块自动初始化，但这些空回调的实际开销可能非常高。</span><span class="sxs-lookup"><span data-stu-id="ced3f-165">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with this code block, these empty callbacks can actually become very expensive.</span></span> <span data-ttu-id="ced3f-166">Unity 在 UnityEngine 代码与应用程序代码之间的非托管/托管代码边界范围内来回操作。</span><span class="sxs-lookup"><span data-stu-id="ced3f-166">Unity operates back and forth over an unmanaged/managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="ced3f-167">通过此桥梁进行上下文切换会产生相当高的开销，即使没有要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="ced3f-167">Context switching over this bridge is fairly expensive, even if there is nothing to execute.</span></span> <span data-ttu-id="ced3f-168">如果应用具有数百个 GameObject 以及包含空重复性 Unity 回调的组件，则此操作特别容易造成问题。</span><span class="sxs-lookup"><span data-stu-id="ced3f-168">This becomes especially problematic if your app has 100's of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="ced3f-169">Update() 最容易造成此性能问题，但如下所列的其他重复性 Unity 回调可能也好不到哪里去，甚至更糟：FixedUpdate()、LateUpdate()、OnPostRender"、OnPreRender()、OnRenderImage() 等。</span><span class="sxs-lookup"><span data-stu-id="ced3f-169">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks, such as the following can be equally as bad, if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="ced3f-170">**偏向于对每帧运行一次的操作**</span><span class="sxs-lookup"><span data-stu-id="ced3f-170">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="ced3f-171">以下 Unity API 是许多全息应用的常用操作。</span><span class="sxs-lookup"><span data-stu-id="ced3f-171">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="ced3f-172">尽管并非总是可行，但这些函数的结果往往只计算一次，然后在整个应用程序中对给定的帧重新利用结果。</span><span class="sxs-lookup"><span data-stu-id="ced3f-172">Although not always possible, the results from these functions can very commonly be computed once and the results re-utilized across the application for a given frame.</span></span>

    <span data-ttu-id="ced3f-173">a) 一般情况下，最好是通过一个专用的单一实例类或服务来处理投影到场景中的视线，然后在所有其他场景组件中重复使用此结果，而无需由每个组件执行重复性的，但本质上相同的光投影操作。</span><span class="sxs-lookup"><span data-stu-id="ced3f-173">a) Generally it is good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then re-use this result in all other scene components, instead of making repeated and essentially identical Raycast operations by each component.</span></span> <span data-ttu-id="ced3f-174">当然，某些应用程序可能要求从不同的原点投射光线，或者针对不同的[图层遮罩](https://docs.unity3d.com/ScriptReference/LayerMask.html)投射光线。</span><span class="sxs-lookup"><span data-stu-id="ced3f-174">Of course, some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    <span data-ttu-id="ced3f-175">b) 通过在 Start()或 Awake() 中[缓存引用](#cache-references)，来避免重复性 Unity 回调（例如 Update()）中的 GetComponent() 操作</span><span class="sxs-lookup"><span data-stu-id="ced3f-175">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>

        UnityEngine.Object.GetComponent()

    <span data-ttu-id="ced3f-176">c) 如果可能，最好是在初始化时实例化所有对象，并使用[对象池](#object-pooling)在应用程序的整个运行时中回收并重复使用 GameObject。</span><span class="sxs-lookup"><span data-stu-id="ced3f-176">c) It is good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and re-use GameObjects throughout runtime of your application</span></span>

        UnityEngine.Object.Instantiate()

3) <span data-ttu-id="ced3f-177">**避免接口和虚拟构造**</span><span class="sxs-lookup"><span data-stu-id="ced3f-177">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="ced3f-178">与利用直接构造或直接函数调用相比，通过接口与直接对象调用函数或调用虚拟函数往往会造成高得多的开销。</span><span class="sxs-lookup"><span data-stu-id="ced3f-178">Invoking function calls through interfaces vs direct objects or calling virtual functions can often times be much more expensive than utilizing direct constructs or direct function calls.</span></span> <span data-ttu-id="ced3f-179">如果不需要虚拟函数或接口，应将其删除。</span><span class="sxs-lookup"><span data-stu-id="ced3f-179">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="ced3f-180">但是，如果利用它们能够简化开发协作、改善代码的易读性和代码可维护性，则这些做法造成的性能下降一般是值得的。</span><span class="sxs-lookup"><span data-stu-id="ced3f-180">However, the performance hit for these approaches are generally worth the trade-off if utilizing them simplifies development collaboration, code readability, and code maintainability.</span></span>

    <span data-ttu-id="ced3f-181">一般情况下，不建议将字段和函数标记为虚拟，除非明确要求覆盖此成员。</span><span class="sxs-lookup"><span data-stu-id="ced3f-181">Generally, the recommendation is to not mark fields and functions as virtual unless there is a clear expectation that this member needs to be overwritten.</span></span> <span data-ttu-id="ced3f-182">应特别注意要对每个帧调用多次（甚至对每个帧调用一次，例如 `UpdateUI()` 方法）的高频代码路径。</span><span class="sxs-lookup"><span data-stu-id="ced3f-182">One should be especially careful around high-frequency code paths that are called many times per frame or even once per frame such as an `UpdateUI()` method.</span></span>

4) <span data-ttu-id="ced3f-183">**避免按值传递结构**</span><span class="sxs-lookup"><span data-stu-id="ced3f-183">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="ced3f-184">与类不同，结构是值类型，将其直接传递给函数时，其内容将复制到新建的实例。</span><span class="sxs-lookup"><span data-stu-id="ced3f-184">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="ced3f-185">这种复制增加了 CPU 开销以及堆栈上的附加内存。</span><span class="sxs-lookup"><span data-stu-id="ced3f-185">This copy adds CPU cost, as well as additional memory on the stack.</span></span> <span data-ttu-id="ced3f-186">对于小型结构，这种影响通常可以忽略不计，因此是可接受的。</span><span class="sxs-lookup"><span data-stu-id="ced3f-186">For small structs, the effect is usually very minimal and thus acceptable.</span></span> <span data-ttu-id="ced3f-187">但是，对于要对每个帧重复调用的函数，以及采用大型结构的函数，如果可能，请修改函数定义以按引用传递。</span><span class="sxs-lookup"><span data-stu-id="ced3f-187">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="ced3f-188">在此处了解详细信息</span><span class="sxs-lookup"><span data-stu-id="ced3f-188">Learn more here</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="ced3f-189">杂项</span><span class="sxs-lookup"><span data-stu-id="ced3f-189">Miscellaneous</span></span>

1) <span data-ttu-id="ced3f-190">**物理学**</span><span class="sxs-lookup"><span data-stu-id="ced3f-190">**Physics**</span></span>

    <span data-ttu-id="ced3f-191">a) 一般情况下，改善物理学的最简单方法是限制花费在物理学上的时间或每秒迭代次数。</span><span class="sxs-lookup"><span data-stu-id="ced3f-191">a) Generally, the easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="ced3f-192">当然，这会降低模拟准确度。</span><span class="sxs-lookup"><span data-stu-id="ced3f-192">Of course, this will reduce simulation accuracy.</span></span> <span data-ttu-id="ced3f-193">参阅 Unity 中的 [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)</span><span class="sxs-lookup"><span data-stu-id="ced3f-193">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="ced3f-194">b) Unity 中的碰撞体类型具有广泛不同的性能特征。</span><span class="sxs-lookup"><span data-stu-id="ced3f-194">b) The type of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="ced3f-195">下面从左到右按顺序列出了性能最高到性能最低的碰撞体。</span><span class="sxs-lookup"><span data-stu-id="ced3f-195">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="ced3f-196">最重要的是避免网格碰撞体，其开销要比基元碰撞体高出太多。</span><span class="sxs-lookup"><span data-stu-id="ced3f-196">It is most important to avoid Mesh Colliders, which are substantially more expensive than the primitive colliders.</span></span>

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    <span data-ttu-id="ced3f-197">有关详细信息，请参阅 [Unity 物理学最佳做法](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="ced3f-197">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="ced3f-198">**动画**</span><span class="sxs-lookup"><span data-stu-id="ced3f-198">**Animations**</span></span>

    <span data-ttu-id="ced3f-199">通过禁用动画程序组件来禁用空闲动画（禁用游戏对象不会产生相同的效果）。</span><span class="sxs-lookup"><span data-stu-id="ced3f-199">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="ced3f-200">避免其动画程序循环将某个值设置为相同内容的设计模式。</span><span class="sxs-lookup"><span data-stu-id="ced3f-200">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="ced3f-201">此方法会产生相当大的开销，但对应用程序没有影响。</span><span class="sxs-lookup"><span data-stu-id="ced3f-201">There is considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="ced3f-202">在此处了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="ced3f-202">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="ced3f-203">**复杂算法**</span><span class="sxs-lookup"><span data-stu-id="ced3f-203">**Complex algorithms**</span></span>

    <span data-ttu-id="ced3f-204">如果应用程序使用复杂算法，例如逆向运动、路径查找等，请努力找到更简单的方法，或调整其性能相关的设置</span><span class="sxs-lookup"><span data-stu-id="ced3f-204">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="ced3f-205">CPU-GPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="ced3f-205">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="ced3f-206">一般情况下，CPU-GPU 性能归根结底与提交到显卡的**绘制调用**相关。</span><span class="sxs-lookup"><span data-stu-id="ced3f-206">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="ced3f-207">为了改善性能，需要战略性地**减少**绘制调用，或**重新构建**绘制调用以获得最佳结果。</span><span class="sxs-lookup"><span data-stu-id="ced3f-207">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="ced3f-208">由于绘制调用本身是资源密集型的，减少此类调用可以减少所需的总体工作量。</span><span class="sxs-lookup"><span data-stu-id="ced3f-208">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="ced3f-209">此外，绘制调用之间的状态更改需要在图形驱动程序中执行高开销的验证和转换步骤，因此，重新构建应用程序的绘制调用来限制状态更改（例如</span><span class="sxs-lookup"><span data-stu-id="ced3f-209">Further, state changes between draw calls requires costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes (i.e</span></span> <span data-ttu-id="ced3f-210">不同的材料等）可以大幅提高性能。</span><span class="sxs-lookup"><span data-stu-id="ced3f-210">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="ced3f-211">Unity 通过一篇详尽的文章概述并深入探讨了如何根据其平台批处理绘制调用。</span><span class="sxs-lookup"><span data-stu-id="ced3f-211">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="ced3f-212">Unity 绘制调用批处理</span><span class="sxs-lookup"><span data-stu-id="ced3f-212">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="ced3f-213">单通道实例化渲染</span><span class="sxs-lookup"><span data-stu-id="ced3f-213">Single pass instanced rendering</span></span>

<span data-ttu-id="ced3f-214">Unity 中的单通道实例化渲染使针对每只眼睛的绘制调用缩减为一个实例化绘制调用。</span><span class="sxs-lookup"><span data-stu-id="ced3f-214">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="ced3f-215">由于两个绘制调用之间的缓存内聚性，GPU 的性能也能得到一定的改善。</span><span class="sxs-lookup"><span data-stu-id="ced3f-215">Due to cache coherency between two draw calls, there is also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="ced3f-216">在 Unity 项目中启用此功能</span><span class="sxs-lookup"><span data-stu-id="ced3f-216">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="ced3f-217">打开“播放器 XR 设置”（转到“编辑” > “项目设置” > “播放器” > “XR 设置”）     </span><span class="sxs-lookup"><span data-stu-id="ced3f-217">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="ced3f-218">从“立体渲染方法”下拉菜单中选择“单通道实例化”（必须选中“支持虚拟现实”复选框）   </span><span class="sxs-lookup"><span data-stu-id="ced3f-218">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="ced3f-219">有关此渲染方法的详细信息，请阅读 Unity 的以下文章。</span><span class="sxs-lookup"><span data-stu-id="ced3f-219">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="ced3f-220">如何使用高级立体渲染最大化 AR 和 VR 的性能</span><span class="sxs-lookup"><span data-stu-id="ced3f-220">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="ced3f-221">单通道实例化</span><span class="sxs-lookup"><span data-stu-id="ced3f-221">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="ced3f-222">如果开发人员的现有自定义着色器不是针对实例化编写的，则单通道实例化渲染会发生一个常见问题。</span><span class="sxs-lookup"><span data-stu-id="ced3f-222">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="ced3f-223">启用此功能后，开发人员可能会注意到，某些 GameObject 只在一只眼睛中呈现。</span><span class="sxs-lookup"><span data-stu-id="ced3f-223">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="ced3f-224">这是因为，关联的自定义着色器没有与实例化相关的适当属性。</span><span class="sxs-lookup"><span data-stu-id="ced3f-224">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="ced3f-225">请参阅 Unity 文章 [HoloLens 的 单通道立体渲染](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)来了解如何解决此问题</span><span class="sxs-lookup"><span data-stu-id="ced3f-225">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="ced3f-226">静态批处理</span><span class="sxs-lookup"><span data-stu-id="ced3f-226">Static batching</span></span>

<span data-ttu-id="ced3f-227">Unity 能够批处理许多静态对象，以减少对 GPU 的绘制调用。</span><span class="sxs-lookup"><span data-stu-id="ced3f-227">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="ced3f-228">静态批处理适用于 Unity 中具有以下特征的大多数[渲染器](https://docs.unity3d.com/ScriptReference/Renderer.html)：**1) 共享相同的材料**；**2) 全部标记为 *Static*** （在 Unity 中选择一个对象，然后单击检查器右上角的复选框）。</span><span class="sxs-lookup"><span data-stu-id="ced3f-228">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and click the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="ced3f-229">标记为 *Static* 的 GameObject 无法在应用程序的整个运行时中移动。</span><span class="sxs-lookup"><span data-stu-id="ced3f-229">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="ced3f-230">因此，在几乎每个对象都需要进行定位、移动、缩放等操作的 HoloLens 上，可能很难利用静态批处理。对于沉浸式头戴显示设备，静态批处理可以大幅减少绘制调用，从而改善性能。</span><span class="sxs-lookup"><span data-stu-id="ced3f-230">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="ced3f-231">有关更多详细信息，请阅读 [Unity 中的绘制调用批处理](https://docs.unity3d.com/Manual/DrawCallBatching.html)下的“静态批处理”。 </span><span class="sxs-lookup"><span data-stu-id="ced3f-231">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="ced3f-232">动态批处理</span><span class="sxs-lookup"><span data-stu-id="ced3f-232">Dynamic batching</span></span>

<span data-ttu-id="ced3f-233">由于在 HoloLens 开发中将对象标记为 *Static* 会造成问题，动态批处理可能是弥补这项短缺功能的极佳手段。</span><span class="sxs-lookup"><span data-stu-id="ced3f-233">Since it is problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="ced3f-234">当然，它也可用于沉浸式头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="ced3f-234">Of course, it can also be useful on immersive headsets, as well.</span></span> <span data-ttu-id="ced3f-235">不过，Unity 中的动态批处理可能很难启用，原因是 GameObject 必须 **a) 共享相同的材料**；**b) 符合其他很多条件**。</span><span class="sxs-lookup"><span data-stu-id="ced3f-235">However, dynamic batching in Unity can be difficult to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="ced3f-236">有关条件的完整列表，请阅读[Unity 中的绘制调用批处理](https://docs.unity3d.com/Manual/DrawCallBatching.html)下的“动态批处理”。 </span><span class="sxs-lookup"><span data-stu-id="ced3f-236">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="ced3f-237">最常见的情况是，由于关联的网格数据不能超过 300 个顶点，因此 GameObject 无效，无法对其进行动态批处理。</span><span class="sxs-lookup"><span data-stu-id="ced3f-237">Most commonly, GameObjects become invalid to be batched dynamically, because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="ced3f-238">其他技术</span><span class="sxs-lookup"><span data-stu-id="ced3f-238">Other techniques</span></span>

<span data-ttu-id="ced3f-239">仅当多个 GameObject 能够共享同一材料时，才会发生批处理。</span><span class="sxs-lookup"><span data-stu-id="ced3f-239">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="ced3f-240">通常，批处理受阻的原因是 GameObject 需要对其各自的材料使用独特的纹理。</span><span class="sxs-lookup"><span data-stu-id="ced3f-240">Typically, this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="ced3f-241">开发人员往往将纹理合并成一个大纹理，此方法称为[纹理集合](https://en.wikipedia.org/wiki/Texture_atlas)。</span><span class="sxs-lookup"><span data-stu-id="ced3f-241">It is common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="ced3f-242">此外，在可能且合理的情况下，他们倾向于将网格合并成一个 GameObject。</span><span class="sxs-lookup"><span data-stu-id="ced3f-242">Furthermore, it is generally preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="ced3f-243">Unity 中的每个渲染器具有自身关联的绘制调用，而不是通过一个渲染器提交合并的网格。</span><span class="sxs-lookup"><span data-stu-id="ced3f-243">Each Renderer in Unity will have its associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span>

>[!NOTE]
> <span data-ttu-id="ced3f-244">在运行时修改 Renderer.material 属性会创建材料的副本，因此可能会中断批处理。</span><span class="sxs-lookup"><span data-stu-id="ced3f-244">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="ced3f-245">使用 Renderer.sharedMaterial 可以修改各个 GameObject 的共享材料属性。</span><span class="sxs-lookup"><span data-stu-id="ced3f-245">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="ced3f-246">GPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="ced3f-246">GPU performance recommendations</span></span>

<span data-ttu-id="ced3f-247">详细了解[如何在 Unity 中优化图形渲染](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span><span class="sxs-lookup"><span data-stu-id="ced3f-247">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span>

### <a name="optimize-depth-buffer-sharing"></a><span data-ttu-id="ced3f-248">优化深度缓冲区共享</span><span class="sxs-lookup"><span data-stu-id="ced3f-248">Optimize depth buffer sharing</span></span>

<span data-ttu-id="ced3f-249">通常建议在“播放器 XR 设置”下启用“深度缓冲区共享”，以优化[全息影像稳定性](Hologram-stability.md)。  </span><span class="sxs-lookup"><span data-stu-id="ced3f-249">It is generally recommended to enable **Depth buffer sharing** under **Player XR Settings** to optimize for [hologram stability](Hologram-stability.md).</span></span> <span data-ttu-id="ced3f-250">但是，在使用此设置的情况下启用基于深度的后期阶段重新投影时，建议选择 **16 位深度格式**而不是 **24 位深度格式**。</span><span class="sxs-lookup"><span data-stu-id="ced3f-250">When enabling depth-based late-stage reprojection with this setting however, it is recommended to select **16-bit depth format** instead of **24-bit depth format**.</span></span> <span data-ttu-id="ced3f-251">16 位深度缓冲区可以大幅减少与深度缓冲区流量相关的带宽（以及电量消耗）。</span><span class="sxs-lookup"><span data-stu-id="ced3f-251">The 16-bit depth buffers will drastically reduce the bandwidth (and thus power) associated with depth buffer traffic.</span></span> <span data-ttu-id="ced3f-252">这可能会给节能和性能提升带来很大的好处。</span><span class="sxs-lookup"><span data-stu-id="ced3f-252">This can be a big win both in power reduction and performance improvement.</span></span> <span data-ttu-id="ced3f-253">但是，使用 *16 位深度格式*可能会造成两种负面影响。</span><span class="sxs-lookup"><span data-stu-id="ced3f-253">However, there are two possible negative outcomes by using *16-bit depth format*.</span></span>

<span data-ttu-id="ced3f-254">**Z 冲突**</span><span class="sxs-lookup"><span data-stu-id="ced3f-254">**Z-Fighting**</span></span>

<span data-ttu-id="ced3f-255">与 24 位相比，16 位的更低深度范围保真度更容易发生 [Z 冲突](https://en.wikipedia.org/wiki/Z-fighting)。</span><span class="sxs-lookup"><span data-stu-id="ced3f-255">The reduced depth range fidelity makes [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) more likely to occur with 16-bit than 24-bit.</span></span> <span data-ttu-id="ced3f-256">若要避免这种假象，请修改 [Unity 相机](https://docs.unity3d.com/Manual/class-Camera.html)的近距/远距剪裁平面，以采用更低的精度。</span><span class="sxs-lookup"><span data-stu-id="ced3f-256">To avoid these artifacts, modify the near/far clip planes of the [Unity camera](https://docs.unity3d.com/Manual/class-Camera.html) to account for the lower precision.</span></span> <span data-ttu-id="ced3f-257">对于基于 HoloLens 的应用程序，50 米（而不是 Unity 的默认 1000 米）的远距剪裁平面通常可以消除任何 Z 冲突。</span><span class="sxs-lookup"><span data-stu-id="ced3f-257">For HoloLens-based applications, a far clip plane of 50m instead of the Unity default 1000m can generally eliminate any z-fighting.</span></span>

<span data-ttu-id="ced3f-258">**已禁用模具缓冲区**</span><span class="sxs-lookup"><span data-stu-id="ced3f-258">**Disabled Stencil Buffer**</span></span>

<span data-ttu-id="ced3f-259">当 Unity 创建 [16 位深度的渲染纹理](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)时，不会创建模具缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ced3f-259">When Unity creates a [Render Texture with 16-bit depth](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), there is no stencil buffer created.</span></span> <span data-ttu-id="ced3f-260">选择 24 位深度格式后，每个 Unity 文档将创建一个 24 位 Z 缓冲区和一个 [8 位模具缓冲区] (https://docs.unity3d.com/Manual/SL-Stencil.html) （如果 32 位在设备上适用，通常在 HoloLens 等设备上适用）。</span><span class="sxs-lookup"><span data-stu-id="ced3f-260">Selecting 24-bit depth format, per Unity documentation, will create a 24-bit z-buffer, as well as an [8-bit stencil buffer] (https://docs.unity3d.com/Manual/SL-Stencil.html) (if 32-bit is applicable on a device, which is generally the case such as HoloLens).</span></span>

### <a name="avoid-full-screen-effects"></a><span data-ttu-id="ced3f-261">避免全屏效果</span><span class="sxs-lookup"><span data-stu-id="ced3f-261">Avoid full-screen effects</span></span>

<span data-ttu-id="ced3f-262">全屏运行的技术可能会产生相当高的开销，因为它们的数量级是每帧数百万次操作。</span><span class="sxs-lookup"><span data-stu-id="ced3f-262">Techniques that operate on the full screen can be quite expensive since their order of magnitude is millions of operations every frame.</span></span> <span data-ttu-id="ced3f-263">因此，建议避免抗锯齿、开花等[后处理](https://docs.unity3d.com/Manual/PostProcessingOverview.html)效果。</span><span class="sxs-lookup"><span data-stu-id="ced3f-263">Thus, it is recommended to avoid [post-processing effects](https://docs.unity3d.com/Manual/PostProcessingOverview.html) such as anti-aliasing, bloom, and more.</span></span>

### <a name="optimal-lighting-settings"></a><span data-ttu-id="ced3f-264">最佳照明设置</span><span class="sxs-lookup"><span data-stu-id="ced3f-264">Optimal lighting settings</span></span>

<span data-ttu-id="ced3f-265">Unity 中的[实时全局照明](https://docs.unity3d.com/Manual/GIIntro.html)可以提供杰出的视觉效果，但涉及到开销很高的照明计算。</span><span class="sxs-lookup"><span data-stu-id="ced3f-265">[Real-time Global Illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide outstanding visual results but involves quite expensive lighting calculations.</span></span> <span data-ttu-id="ced3f-266">建议通过“窗口” > “渲染” > “照明设置”> 取消选中“实时全局照明”，为每个 Unity 场景文件禁用“实时全局照明”。    </span><span class="sxs-lookup"><span data-stu-id="ced3f-266">It is recommended to disable Realtime Global Illumination for every Unity scene file via **Window** > **Rendering** > **Lighting Settings** > Uncheck **Real-time Global Illumination**.</span></span>

<span data-ttu-id="ced3f-267">此外，建议禁用所有阴影投射，因为这也会将高开销的 GPU 通道添加到 Unity 场景中。</span><span class="sxs-lookup"><span data-stu-id="ced3f-267">Furthermore, it is recommended to disable all shadow casting as these also add expensive GPU passes onto a Unity scene.</span></span> <span data-ttu-id="ced3f-268">可以按光源禁用阴影，但也可以通过“质量”设置对其进行整体控制。</span><span class="sxs-lookup"><span data-stu-id="ced3f-268">Shadows can be disable per light but can also be controlled holistically via Quality settings.</span></span>

<span data-ttu-id="ced3f-269">转到“编辑” > “项目设置”，然后选择“质量”类别 > 为“UWP 平台”选择“低质量”。    </span><span class="sxs-lookup"><span data-stu-id="ced3f-269">**Edit** > **Project Settings**, then select the **Quality** category > Select **Low Quality** for the UWP Platform.</span></span> <span data-ttu-id="ced3f-270">还可以直接将“阴影”属性设置为“禁用阴影”。  </span><span class="sxs-lookup"><span data-stu-id="ced3f-270">One can also just set the **Shadows** property to **Disable Shadows**.</span></span>

### <a name="reduce-poly-count"></a><span data-ttu-id="ced3f-271">减少多边形计数</span><span class="sxs-lookup"><span data-stu-id="ced3f-271">Reduce poly count</span></span>

<span data-ttu-id="ced3f-272">通常可通过以下方式减少多边形计数</span><span class="sxs-lookup"><span data-stu-id="ced3f-272">Polygon count is usually reduced by either</span></span>
1) <span data-ttu-id="ced3f-273">从场景中删除对象</span><span class="sxs-lookup"><span data-stu-id="ced3f-273">Removing objects from a scene</span></span>
2) <span data-ttu-id="ced3f-274">抽离资产，以减少给定网格的多边形数目</span><span class="sxs-lookup"><span data-stu-id="ced3f-274">Asset decimation which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="ced3f-275">在应用程序中实施[详细级别 (LOD) 系统](https://docs.unity3d.com/Manual/LevelOfDetail.html)，以通过同一几何结构的较小多边形版本渲染远距离对象</span><span class="sxs-lookup"><span data-stu-id="ced3f-275">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application which renders far away objects with lower-polygon version of the same geometry</span></span>

### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="ced3f-276">了解 Unity 中的着色器</span><span class="sxs-lookup"><span data-stu-id="ced3f-276">Understanding shaders in Unity</span></span>

<span data-ttu-id="ced3f-277">若要大致比较着色器的性能，一种简单方法是识别每个着色器在运行时执行的平均操作数目。</span><span class="sxs-lookup"><span data-stu-id="ced3f-277">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="ced3f-278">可在 Unity 中轻松实现此目的。</span><span class="sxs-lookup"><span data-stu-id="ced3f-278">This can be done easily in Unity.</span></span>

1) <span data-ttu-id="ced3f-279">选择着色器资产或选择材料，然后在检查器窗口的右上角选择齿轮图标，然后选择“选择着色器” </span><span class="sxs-lookup"><span data-stu-id="ced3f-279">Select your shader asset or select a material, then in the top right corner of the inspector window, select the gear icon followed by **"Select Shader"**</span></span>

    ![在 Unity 中选择着色器](images/Select-shader-unity.png)
2) <span data-ttu-id="ced3f-281">选择着色器资产后，单击检查器窗口下的“编译并显示代码”按钮 </span><span class="sxs-lookup"><span data-stu-id="ced3f-281">With the shader asset selected, click the **"Compile and show code"** button under the inspector window</span></span>

    ![在 Unity 中编译着色器代码](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="ced3f-283">编译后，查看结果中的统计信息部分，其中包含针对顶点和像素着色器（注意：像素着色器通常也称为段着色器）执行的不同操作数目</span><span class="sxs-lookup"><span data-stu-id="ced3f-283">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity 标准着色器操作](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a><span data-ttu-id="ced3f-285">优化像素着色器</span><span class="sxs-lookup"><span data-stu-id="ced3f-285">Optimize pixel shaders</span></span>

<span data-ttu-id="ced3f-286">使用上述方法查看编译的统计信息结果时可以看到，[段着色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)执行的平均操作数目通常比[顶点着色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)更多。</span><span class="sxs-lookup"><span data-stu-id="ced3f-286">Looking at the compiled statistic results using the method above, the [fragment shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) will generally execute more operations than the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders), on average.</span></span> <span data-ttu-id="ced3f-287">段着色器（也称为像素着色器）是按屏幕输出中的像素执行的，而顶点着色器只是按屏幕上绘制的所有网格的每个顶点执行的。</span><span class="sxs-lookup"><span data-stu-id="ced3f-287">The fragment shader, also known as the pixel shader, is executed per pixel on the screen output while the vertex shader is only executed per-vertex of all meshes being drawn to the screen.</span></span> 

<span data-ttu-id="ced3f-288">因此，段着色器不仅仅是指令数比顶点着色器更多（因为要执行所有照明计算），而且段着色器几乎总是针对较大数据集执行的。</span><span class="sxs-lookup"><span data-stu-id="ced3f-288">Thus, not only do fragment shaders have more instructions than vertex shaders because of all the lighting calculations, fragment shaders are almost always executed on a larger dataset.</span></span> <span data-ttu-id="ced3f-289">例如，如果屏幕输出为 2,000 x 2,000 图像，则段着色器可能会执行 2,000\*2,000 = 4,000,000 次。</span><span class="sxs-lookup"><span data-stu-id="ced3f-289">For example, if the screen output is a 2k by 2k image, then the fragment shader can get executed 2,000\*2,000 = 4,000,000 times.</span></span> <span data-ttu-id="ced3f-290">如果渲染两只眼睛，此数字将会翻倍，因为有两个屏幕。</span><span class="sxs-lookup"><span data-stu-id="ced3f-290">If rendering two eyes, this number doubles since there are two screens.</span></span> <span data-ttu-id="ced3f-291">如果混合现实应用程序使用多个通道、全屏后处理效果或以相同的像素渲染多个网格，则此数字会大幅提高。</span><span class="sxs-lookup"><span data-stu-id="ced3f-291">If a mixed reality application has multiple passes, full-screen post-processing effects, or rendering multiple meshes to the same pixel, this number will increase dramatically.</span></span> 

<span data-ttu-id="ced3f-292">因此，在段着色器中减少操作数目所带来的性能增益，通常远远好过在顶点着色器中进行优化。</span><span class="sxs-lookup"><span data-stu-id="ced3f-292">Therefore, reducing the number of operations in the fragment shader can generally give far greater performance gains over optimizations in the vertex shader.</span></span>

#### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="ced3f-293">Unity 标准着色器替代技术</span><span class="sxs-lookup"><span data-stu-id="ced3f-293">Unity Standard shader alternatives</span></span>

<span data-ttu-id="ced3f-294">不要使用基于物理学的渲染 (PBR) 或其他优质着色器，而是寻求利用更高性能且更经济的着色器。</span><span class="sxs-lookup"><span data-stu-id="ced3f-294">Instead of using a physically based rendering (PBR) or another high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="ced3f-295">[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供针对混合现实项目进行优化的 [MRTK 标准着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)。</span><span class="sxs-lookup"><span data-stu-id="ced3f-295">The [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides the [MRTK standard shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="ced3f-296">与 Unity 标准着色器相比，Unity 还提供不发光、顶点发亮、漫射和其他简化的着色器选项。</span><span class="sxs-lookup"><span data-stu-id="ced3f-296">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are significantly faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="ced3f-297">有关更多详细信息，请参阅[内置着色器的用法和性能](https://docs.unity3d.com/Manual/shader-Performance.html)。</span><span class="sxs-lookup"><span data-stu-id="ced3f-297">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

#### <a name="shader-preloading"></a><span data-ttu-id="ced3f-298">着色器预加载</span><span class="sxs-lookup"><span data-stu-id="ced3f-298">Shader preloading</span></span>

<span data-ttu-id="ced3f-299">使用着色器预加载和其他技巧优化[着色器加载时间](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)。 </span><span class="sxs-lookup"><span data-stu-id="ced3f-299">Use *Shader preloading* and other tricks to optimize [shader load time](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html).</span></span> <span data-ttu-id="ced3f-300">具体而言，着色器预加载意味着不会看到运行时着色器编译造成的任何帧聚结情况。</span><span class="sxs-lookup"><span data-stu-id="ced3f-300">In particular, shader preloading means you won't see any hitches due to runtime shader compilation.</span></span>

### <a name="limit-overdraw"></a><span data-ttu-id="ced3f-301">限制过度绘制</span><span class="sxs-lookup"><span data-stu-id="ced3f-301">Limit overdraw</span></span>

<span data-ttu-id="ced3f-302">在 Unity 中，可以通过在“场景”视图的左上角切换[**绘制模式菜单**](https://docs.unity3d.com/Manual/ViewModes.html)并选择“过度绘制”，来显示其场景的过度绘制。  </span><span class="sxs-lookup"><span data-stu-id="ced3f-302">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top-left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="ced3f-303">一般情况下，在将对象发送到 GPU 之前提前剔除对象可以缓解过度绘制。</span><span class="sxs-lookup"><span data-stu-id="ced3f-303">Generally, overdraw can be mitigated by culling objects ahead of time before they are sent to the GPU.</span></span> <span data-ttu-id="ced3f-304">Unity 提供了有关为其引擎实现[遮挡剔除](https://docs.unity3d.com/Manual/OcclusionCulling.html)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ced3f-304">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="ced3f-305">内存建议</span><span class="sxs-lookup"><span data-stu-id="ced3f-305">Memory recommendations</span></span>

<span data-ttu-id="ced3f-306">过多的内存分配和解除分配操作可能对全息应用程序产生负面影响，导致性能不稳定、帧冻结和其他不利行为。</span><span class="sxs-lookup"><span data-stu-id="ced3f-306">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application, resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="ced3f-307">在 Unity 中进行开发时，了解内存注意事项特别重要，因为内存管理由垃圾回收器进行控制。</span><span class="sxs-lookup"><span data-stu-id="ced3f-307">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="ced3f-308">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="ced3f-308">Garbage collection</span></span>

<span data-ttu-id="ced3f-309">在执行期间激活垃圾回收器 (GC) 来分析不再处于范围内的对象时，如果需要释放对象的内存以便可供重复使用，则全息应用会将处理计算时间损失在 GC 上。</span><span class="sxs-lookup"><span data-stu-id="ced3f-309">Holographic apps will lose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released, so it can be made available for re-use.</span></span> <span data-ttu-id="ced3f-310">连续的分配和解除分配通常需要垃圾回收器更频繁地运行，因此会损害性能和用户体验。</span><span class="sxs-lookup"><span data-stu-id="ced3f-310">Constant allocations and de-allocations will generally require the garbage collector to run more frequently, thus hurting performance and user experience.</span></span>

<span data-ttu-id="ced3f-311">Unity 在一个很好的网页中详细说明了垃圾回收器的工作原理，并提供了有关如何为内存管理编写更高效代码的提示。</span><span class="sxs-lookup"><span data-stu-id="ced3f-311">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="ced3f-312">优化 Unity 游戏中的垃圾回收</span><span class="sxs-lookup"><span data-stu-id="ced3f-312">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="ced3f-313">导致过度垃圾回收的最常见原因之一是在 Unity 开发中不缓存对组件和类的引用。</span><span class="sxs-lookup"><span data-stu-id="ced3f-313">One of the most common practices that leads to excessive garbage collection is not caching references to components and classes in Unity development.</span></span> <span data-ttu-id="ced3f-314">应在运行 Start() 或 Awake() 期间捕获所有引用，并在以后运行 Update() 或 LateUpdate() 等函数期间重复使用这些引用。</span><span class="sxs-lookup"><span data-stu-id="ced3f-314">Any references should be captured during Start() or Awake() and re-used in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="ced3f-315">其他快速提示：</span><span class="sxs-lookup"><span data-stu-id="ced3f-315">Other quick tips:</span></span>
- <span data-ttu-id="ced3f-316">在运行时使用 [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# 类动态生成复杂字符串</span><span class="sxs-lookup"><span data-stu-id="ced3f-316">Use the [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="ced3f-317">删除不再需要的 Debug.Log() 调用，因为它们仍会在应用的所有生成版本中执行</span><span class="sxs-lookup"><span data-stu-id="ced3f-317">Remove calls to Debug.Log() when no longer needed, as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="ced3f-318">如果全息应用通常需要大量的内存，请考虑在加载阶段（例如，在演示加载或过渡屏幕时）调用 [ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)</span><span class="sxs-lookup"><span data-stu-id="ced3f-318">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="ced3f-319">对象池</span><span class="sxs-lookup"><span data-stu-id="ced3f-319">Object pooling</span></span>

<span data-ttu-id="ced3f-320">对象池是一种热门技术，可以降低对象连续分配和解除分配所造成的开销。</span><span class="sxs-lookup"><span data-stu-id="ced3f-320">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="ced3f-321">此技术是通过以下方式实现的：分配一个由相同对象构成的较大池并重复使用此池中非活动的可用实例，而不是在各个时间内不断生成和销毁对象。</span><span class="sxs-lookup"><span data-stu-id="ced3f-321">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="ced3f-322">对象池非常适合应用中生存期可变的可重用组件。</span><span class="sxs-lookup"><span data-stu-id="ced3f-322">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="ced3f-323">Unity 中的对象池教程</span><span class="sxs-lookup"><span data-stu-id="ced3f-323">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="ced3f-324">启动性能</span><span class="sxs-lookup"><span data-stu-id="ced3f-324">Startup performance</span></span>

<span data-ttu-id="ced3f-325">应考虑使用较小的场景启动应用，然后使用 *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 加载场景的剩余部分。</span><span class="sxs-lookup"><span data-stu-id="ced3f-325">You should consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="ced3f-326">这样，应用就可以尽快进入交互状态。</span><span class="sxs-lookup"><span data-stu-id="ced3f-326">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="ced3f-327">请注意，在激活新场景时，可能会出现较大的 CPU 峰值，并且渲染的任何内容可能会出现断连或聚结。</span><span class="sxs-lookup"><span data-stu-id="ced3f-327">Be aware that there may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="ced3f-328">解决此问题的方法之一是，在所要加载的场景中将 AsyncOperation.allowSceneActivation 属性设置为“false”，等待场景加载完成，将屏幕清理为黑屏，然后将此属性重新设置为“true”以完成场景激活。</span><span class="sxs-lookup"><span data-stu-id="ced3f-328">One way to work around this is to set the AsyncOperation.allowSceneActivation property to "false" on the scene being loaded, wait for the scene to load, clear the screen to black, and then set it back to "true" to complete the scene activation.</span></span>

<span data-ttu-id="ced3f-329">请记住，在加载启动场景时，会向用户显示全息初始屏幕。</span><span class="sxs-lookup"><span data-stu-id="ced3f-329">Remember that while the startup scene is loading, the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="ced3f-330">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ced3f-330">See also</span></span>
- [<span data-ttu-id="ced3f-331">优化 Unity 游戏中的图形渲染</span><span class="sxs-lookup"><span data-stu-id="ced3f-331">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="ced3f-332">优化 Unity 游戏中的垃圾回收</span><span class="sxs-lookup"><span data-stu-id="ced3f-332">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="ced3f-333">[物理学最佳做法 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="ced3f-333">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="ced3f-334">[优化脚本 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="ced3f-334">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>
