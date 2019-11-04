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
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="205c2-104">Unity 性能建议</span><span class="sxs-lookup"><span data-stu-id="205c2-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="205c2-105">本文基于[混合现实的性能建议](understanding-performance-for-mixed-reality.md)中所述的讨论，但重点介绍特定于 Unity 引擎环境的知识。</span><span class="sxs-lookup"><span data-stu-id="205c2-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unity engine environment.</span></span>

<span data-ttu-id="205c2-106">同时，强烈建议开发人员查看[Unity 项目的推荐环境设置](Recommended-settings-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="205c2-106">It is also highly advisable that developers review the [recommended environment settings for Unity article](Recommended-settings-for-unity.md).</span></span> <span data-ttu-id="205c2-107">本文提供了一些内容，其中包含一些最重要的场景配置，用于构建性能混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="205c2-107">This article has content with some of the most important scene configurations in regards to building performant Mixed Reality apps.</span></span> <span data-ttu-id="205c2-108">下面突出显示了其中一些推荐的设置。</span><span class="sxs-lookup"><span data-stu-id="205c2-108">Some of these recommended settings are highlighted below as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="205c2-109">如何用 Unity 进行分析</span><span class="sxs-lookup"><span data-stu-id="205c2-109">How to profile with Unity</span></span>

<span data-ttu-id="205c2-110">Unity 提供了 **[Unity 探查器](https://docs.unity3d.com/Manual/Profiler.html)** ，这是一个很好的资源，可为你的特定应用收集宝贵的性能见解。</span><span class="sxs-lookup"><span data-stu-id="205c2-110">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="205c2-111">尽管可以在编辑器中运行探查器，但这些度量值并不表示真正的运行时环境，因此应该谨慎使用。</span><span class="sxs-lookup"><span data-stu-id="205c2-111">Although one can run the profiler in-editor, these metrics do not represent the true runtime environment and thus, results from this should be used cautiously.</span></span> <span data-ttu-id="205c2-112">建议在设备上运行时远程分析应用程序，以获得最准确且可操作的见解。</span><span class="sxs-lookup"><span data-stu-id="205c2-112">It is recommended to remotely profile your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="205c2-113">此外，Unity 的[框架调试程序](https://docs.unity3d.com/Manual/FrameDebugger.html)也是一个非常强大的工具，可供使用。</span><span class="sxs-lookup"><span data-stu-id="205c2-113">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)  is also a very powerful and insight tool to utilize.</span></span>

<span data-ttu-id="205c2-114">Unity 为以下方面提供了强大的文档：</span><span class="sxs-lookup"><span data-stu-id="205c2-114">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="205c2-115">如何[远程将 Unity 探查器连接到 UWP 应用程序](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span><span class="sxs-lookup"><span data-stu-id="205c2-115">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="205c2-116">如何[通过 Unity 探查器有效地诊断性能问题](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span><span class="sxs-lookup"><span data-stu-id="205c2-116">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="205c2-117">当 Unity 探查器已连接并在添加 GPU 探查器后（请参阅右上角的 "*添加探查器*"），可以在探查器中间分别查看在 CPU 上花费了多少时间 & GPU。</span><span class="sxs-lookup"><span data-stu-id="205c2-117">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="205c2-118">这允许开发人员在其应用程序是 CPU 或 GPU 限制的情况下获得快速近似值。</span><span class="sxs-lookup"><span data-stu-id="205c2-118">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU 与 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="205c2-120">CPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="205c2-120">CPU performance recommendations</span></span>

<span data-ttu-id="205c2-121">以下内容介绍了更深入的性能做法，尤其针对 Unity & C#开发。</span><span class="sxs-lookup"><span data-stu-id="205c2-121">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="205c2-122">缓存引用</span><span class="sxs-lookup"><span data-stu-id="205c2-122">Cache references</span></span>

<span data-ttu-id="205c2-123">最佳做法是在初始化时缓存对所有相关组件和 Gameobject 的引用。</span><span class="sxs-lookup"><span data-stu-id="205c2-123">It is best practice to cache references to all relevant components and GameObjects at initialization.</span></span> <span data-ttu-id="205c2-124">这是因为重复函数调用（如 *[GetComponent\<t > （）](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 相对于存储指针所需的内存成本要高得多。</span><span class="sxs-lookup"><span data-stu-id="205c2-124">This is because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* are significantly more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="205c2-125">这也适用于经常使用的[相机。](https://docs.unity3d.com/ScriptReference/Camera-main.html)</span><span class="sxs-lookup"><span data-stu-id="205c2-125">This also applies to to the very, regularly used [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).</span></span> <span data-ttu-id="205c2-126">*摄影机*实际上只是使用 *[FindGameObjectsWithTag （）](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* ，低廉在其下使用 *"MainCamera"* 标记在场景图中搜索相机对象。</span><span class="sxs-lookup"><span data-stu-id="205c2-126">*Camera.main* actually just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

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
> <span data-ttu-id="205c2-127">避免 GetComponent （字符串）</span><span class="sxs-lookup"><span data-stu-id="205c2-127">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="205c2-128">使用 *[GetComponent （）](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 时，有少量的不同重载。</span><span class="sxs-lookup"><span data-stu-id="205c2-128">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="205c2-129">应始终使用基于类型的实现，而不是基于字符串的搜索重载，这一点非常重要。</span><span class="sxs-lookup"><span data-stu-id="205c2-129">It is important to always use the Type based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="205c2-130">在场景中按字符串搜索比按类型搜索要大得多。</span><span class="sxs-lookup"><span data-stu-id="205c2-130">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="205c2-131">良好Component GetComponent （类型类型）</span><span class="sxs-lookup"><span data-stu-id="205c2-131">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="205c2-132">良好T GetComponent\<T > （）</span><span class="sxs-lookup"><span data-stu-id="205c2-132">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="205c2-133">Dfx组件 GetComponent （字符串） ></span><span class="sxs-lookup"><span data-stu-id="205c2-133">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="205c2-134">避免成本高昂的操作</span><span class="sxs-lookup"><span data-stu-id="205c2-134">Avoid expensive operations</span></span>

1) <span data-ttu-id="205c2-135">**避免使用[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span><span class="sxs-lookup"><span data-stu-id="205c2-135">**Avoid use of [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="205c2-136">尽管 LINQ 可以非常简洁、易于读写，但它通常需要更多的计算和更多的内存分配，而不是手动写入算法。</span><span class="sxs-lookup"><span data-stu-id="205c2-136">Although LINQ can be very clean and easy to read and write, it generally requires much more computation and particularly more memory allocation than writing the algorithm out manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="205c2-137">**公共 Unity Api**</span><span class="sxs-lookup"><span data-stu-id="205c2-137">**Common Unity APIs**</span></span>

    <span data-ttu-id="205c2-138">某些 Unity Api 虽然有用，但执行起来可能非常昂贵。</span><span class="sxs-lookup"><span data-stu-id="205c2-138">Certain Unity APIs, although useful, can be very expensive to execute.</span></span> <span data-ttu-id="205c2-139">其中的大多数都涉及在整个场景图中搜索 Gameobject 的一些匹配列表。</span><span class="sxs-lookup"><span data-stu-id="205c2-139">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="205c2-140">通常可以通过缓存引用或实现 Gameobject 中的管理器组件来避免这些操作，以跟踪运行时的引用。</span><span class="sxs-lookup"><span data-stu-id="205c2-140">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects in question to track the references at runtime.</span></span>

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> <span data-ttu-id="205c2-141">应该消除 *[SendMessage （）](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 和 *[BroadcastMessage （）](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 。</span><span class="sxs-lookup"><span data-stu-id="205c2-141">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="205c2-142">这些函数的顺序可能比直接函数调用慢1000倍。</span><span class="sxs-lookup"><span data-stu-id="205c2-142">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="205c2-143">**注意装箱**</span><span class="sxs-lookup"><span data-stu-id="205c2-143">**Beware of boxing**</span></span>

    <span data-ttu-id="205c2-144">[装箱](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)是C#语言和运行时的核心概念。</span><span class="sxs-lookup"><span data-stu-id="205c2-144">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="205c2-145">它是将值类型化变量（如 char、int、bool 等）包装到引用类型变量的过程。</span><span class="sxs-lookup"><span data-stu-id="205c2-145">It is the process of wrapping value-typed variables such as char, int, bool, etc. into reference-typed variables.</span></span> <span data-ttu-id="205c2-146">当值类型的变量为 "装箱" 时，它将包装在存储在托管堆上的 System.object 内。</span><span class="sxs-lookup"><span data-stu-id="205c2-146">When a value-typed variable is "boxed", it is wrapped inside of a System.Object which is stored on the managed heap.</span></span> <span data-ttu-id="205c2-147">因此，内存将被分配，最终当必须由垃圾回收器处理时，必须处理内存。</span><span class="sxs-lookup"><span data-stu-id="205c2-147">Thus, memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="205c2-148">这些分配和释放会产生性能开销，在许多情况下都是不必要的，或者可以轻松地将其替换为开销较低的替代项。</span><span class="sxs-lookup"><span data-stu-id="205c2-148">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

    <span data-ttu-id="205c2-149">开发中最常见的装箱形式之一是使用[可以为 null 的值类型](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)。</span><span class="sxs-lookup"><span data-stu-id="205c2-149">One of the most common forms of boxing in development is the use of [nullable value types](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/).</span></span> <span data-ttu-id="205c2-150">当操作可能无法尝试获取值时，通常需要能够在函数中返回值类型为 null 的情况。</span><span class="sxs-lookup"><span data-stu-id="205c2-150">It is common to want to be able to return null for a value type in a function especially when the operation may fail trying to get the value.</span></span> <span data-ttu-id="205c2-151">此方法可能存在的问题是，分配现在发生在堆上，因此需要在以后对其进行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="205c2-151">The potential problem with this approach is that allocation now occur on the heap and consequently need to be garbage collected later.</span></span>

    <span data-ttu-id="205c2-152">**中的装箱示例C#**</span><span class="sxs-lookup"><span data-stu-id="205c2-152">**Example of boxing in C#**</span></span>

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    <span data-ttu-id="205c2-153">**通过可为 null 的值类型进行装箱的示例**</span><span class="sxs-lookup"><span data-stu-id="205c2-153">**Example of problematic boxing via nullable value types**</span></span>

    <span data-ttu-id="205c2-154">此代码演示一个虚拟粒子类，该类可以在 Unity 项目中创建。</span><span class="sxs-lookup"><span data-stu-id="205c2-154">This code demonstrates a dummy particle class that one may create in a Unity project.</span></span> <span data-ttu-id="205c2-155">对 `TryGetSpeed()` 的调用将导致堆上的对象分配，需要在以后的某个时间点对该对象进行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="205c2-155">A call to `TryGetSpeed()` will cause object allocation on the heap which will need to be garbage collected at a later point in time.</span></span> <span data-ttu-id="205c2-156">此示例尤其有问题，因为场景中可能有1000个或更多粒子，每个粒子都要求提供当前速度。</span><span class="sxs-lookup"><span data-stu-id="205c2-156">This example is particularly problematic as there may be 1000+ or many more particles in a scene, each being asked for their current speed.</span></span> <span data-ttu-id="205c2-157">因此，将分配1000个对象，因而每个帧都将释放，这会大大降低性能。</span><span class="sxs-lookup"><span data-stu-id="205c2-157">Thus, 1000's of objects would be allocated and consequently de-allocated every frame which would greatly diminish performance.</span></span> <span data-ttu-id="205c2-158">重新编写函数以返回一个负值（例如-1），以指示失败将避免此问题并使内存在堆栈上。</span><span class="sxs-lookup"><span data-stu-id="205c2-158">Re-writing the function to return a negative value such as -1 to indicate a failure would avoid this issue and keep memory on the stack.</span></span>

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

#### <a name="repeating-code-paths"></a><span data-ttu-id="205c2-159">重复代码路径</span><span class="sxs-lookup"><span data-stu-id="205c2-159">Repeating code paths</span></span>

<span data-ttu-id="205c2-160">任何重复的 Unity 回调函数（即</span><span class="sxs-lookup"><span data-stu-id="205c2-160">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="205c2-161">更新），则应仔细编写每秒和/或帧的多次执行。</span><span class="sxs-lookup"><span data-stu-id="205c2-161">Update) that are executed many times per second and/or frame should be written very carefully.</span></span> <span data-ttu-id="205c2-162">此处的任何昂贵操作都将对性能产生巨大的一致性影响。</span><span class="sxs-lookup"><span data-stu-id="205c2-162">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="205c2-163">**空回调函数**</span><span class="sxs-lookup"><span data-stu-id="205c2-163">**Empty callback functions**</span></span>

    <span data-ttu-id="205c2-164">尽管下面的代码在应用程序中可能看似不合法，尤其是由于每个 Unity 脚本都是通过此代码块自动初始化的，因此这些空回调实际上可能会非常昂贵。</span><span class="sxs-lookup"><span data-stu-id="205c2-164">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with this code block, these empty callbacks can actually become very expensive.</span></span> <span data-ttu-id="205c2-165">Unity 在 UnityEngine 代码和应用程序代码之间的非托管/托管代码边界之间来回操作。</span><span class="sxs-lookup"><span data-stu-id="205c2-165">Unity operates back and forth over an unmanaged/managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="205c2-166">即使没有要执行的操作，通过此桥的上下文切换也相当昂贵。</span><span class="sxs-lookup"><span data-stu-id="205c2-166">Context switching over this bridge is fairly expensive even if there is nothing to execute.</span></span> <span data-ttu-id="205c2-167">如果你的应用程序的 Gameobject 与具有空的重复 Unity 回调的组件具有100个，这会变得非常有问题。</span><span class="sxs-lookup"><span data-stu-id="205c2-167">This becomes especially problematic if your app has 100's of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="205c2-168">Update （）是此性能问题的最常见表现形式，但其他重复 Unity 回调（如以下）可能会像下面那样糟糕： FixedUpdate （）、Behaviour （）、OnPostRender、OnPreRender （）、OnRenderImage （）等。</span><span class="sxs-lookup"><span data-stu-id="205c2-168">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks such as the following can be equally as bad if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="205c2-169">**针对每个帧运行一次的操作**</span><span class="sxs-lookup"><span data-stu-id="205c2-169">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="205c2-170">以下 Unity Api 是许多全息应用的常见操作。</span><span class="sxs-lookup"><span data-stu-id="205c2-170">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="205c2-171">尽管并非总是可行，但这些函数的结果通常也可以计算一次，并且会在应用程序中为给定帧重新利用结果。</span><span class="sxs-lookup"><span data-stu-id="205c2-171">Although not always possible, the results from these functions can very commonly be computed once and the results re-utilized across the application for a given frame.</span></span>

    <span data-ttu-id="205c2-172">答：使用专用的单独类或服务，可以将您的注视 Raycast 处理到场景中，然后在所有其他场景组件中重复使用此结果，而不是每组件.</span><span class="sxs-lookup"><span data-stu-id="205c2-172">a) Generally it is good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then re-use this result in all other scene components, instead of making repeated and essentially identical Raycast operations by each component.</span></span> <span data-ttu-id="205c2-173">当然，某些应用程序可能需要来自不同来源的 raycasts 或不同的[LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)。</span><span class="sxs-lookup"><span data-stu-id="205c2-173">Of course, some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    <span data-ttu-id="205c2-174">b）通过在 Start （）或唤醒（）中[缓存引用](#cache-references)来避免重复的 Unity 回调（如 Update （））中的 GetComponent （）操作</span><span class="sxs-lookup"><span data-stu-id="205c2-174">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>

        UnityEngine.Object.GetComponent()

    <span data-ttu-id="205c2-175">c）最好在初始化时实例化所有对象，并在应用程序运行时使用[对象池](#object-pooling)来回收和重复使用 Gameobject，这是一种很好的做法。</span><span class="sxs-lookup"><span data-stu-id="205c2-175">c) It is good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and re-use GameObjects throughout runtime of your application</span></span>

        UnityEngine.Object.Instantiate()

3) <span data-ttu-id="205c2-176">**避免接口和虚拟构造**</span><span class="sxs-lookup"><span data-stu-id="205c2-176">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="205c2-177">与使用直接构造或直接函数调用相比，通过接口调用函数调用和直接对象或调用虚函数通常会更昂贵。</span><span class="sxs-lookup"><span data-stu-id="205c2-177">Invoking function calls through interfaces vs direct objects or calling virtual functions can often times be much more expensive than utilizing direct constructs or direct function calls.</span></span> <span data-ttu-id="205c2-178">如果不需要虚拟函数或接口，则应将其删除。</span><span class="sxs-lookup"><span data-stu-id="205c2-178">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="205c2-179">不过，如果利用它们来简化开发协作、代码可读性和代码可维护性，通常值得权衡这些方法的性能。</span><span class="sxs-lookup"><span data-stu-id="205c2-179">However, the performance hit for these approaches are generally worth the trade-off if utilizing them simplifies development collaboration, code readability, and code maintainability.</span></span>

    <span data-ttu-id="205c2-180">通常，建议不要将字段和函数标记为虚拟，除非明确要求覆盖此成员。</span><span class="sxs-lookup"><span data-stu-id="205c2-180">Generally, the recommendation is to not mark fields and functions as virtual unless there is a clear expectation that this member needs to be overwritten.</span></span> <span data-ttu-id="205c2-181">应特别注意每个帧调用了多次（甚至每帧一次，例如 `UpdateUI()` 方法）的高频代码路径。</span><span class="sxs-lookup"><span data-stu-id="205c2-181">One should be especially careful around high-frequency code paths that are called many times per frame or even once per frame such as an `UpdateUI()` method.</span></span>

4) <span data-ttu-id="205c2-182">**避免通过值传递结构**</span><span class="sxs-lookup"><span data-stu-id="205c2-182">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="205c2-183">与类不同的是，结构是值类型，并在直接传递到函数时，将其内容复制到新创建的实例。</span><span class="sxs-lookup"><span data-stu-id="205c2-183">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="205c2-184">此副本增加了 CPU 开销以及堆栈上的额外内存。</span><span class="sxs-lookup"><span data-stu-id="205c2-184">This copy adds CPU cost as well as additional memory on the stack.</span></span> <span data-ttu-id="205c2-185">对于小型结构，效果通常非常小，因此是可接受的。</span><span class="sxs-lookup"><span data-stu-id="205c2-185">For small structs, the effect is usually very minimal and thus acceptable.</span></span> <span data-ttu-id="205c2-186">但是，对于每个帧以及采用大型结构的函数重复调用的函数，如果可能，请修改函数定义以通过引用传递。</span><span class="sxs-lookup"><span data-stu-id="205c2-186">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="205c2-187">在此处了解详细信息</span><span class="sxs-lookup"><span data-stu-id="205c2-187">Learn more here</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="205c2-188">其他</span><span class="sxs-lookup"><span data-stu-id="205c2-188">Miscellaneous</span></span>

1) <span data-ttu-id="205c2-189">**物理**</span><span class="sxs-lookup"><span data-stu-id="205c2-189">**Physics**</span></span>

    <span data-ttu-id="205c2-190">a）一般来说，提高物理学的最简单方法是限制在物理学上花费的时间量或每秒迭代的次数。</span><span class="sxs-lookup"><span data-stu-id="205c2-190">a) Generally, easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="205c2-191">当然，这会降低模拟准确性。</span><span class="sxs-lookup"><span data-stu-id="205c2-191">Of course, this will reduce simulation accuracy.</span></span> <span data-ttu-id="205c2-192">请参阅 Unity 中的[TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)</span><span class="sxs-lookup"><span data-stu-id="205c2-192">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="205c2-193">b） Unity 中的 colliders 类型具有广泛不同的性能特征。</span><span class="sxs-lookup"><span data-stu-id="205c2-193">b) The type of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="205c2-194">下面的顺序列出了从左到右的最 colliders 高性能 colliders 的最高性能。</span><span class="sxs-lookup"><span data-stu-id="205c2-194">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="205c2-195">最重要的是避免网格 Colliders，这比基元 Colliders 大得多。</span><span class="sxs-lookup"><span data-stu-id="205c2-195">It is most important to avoid Mesh Colliders which are substantially more expensive than the primitive colliders.</span></span>

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    <span data-ttu-id="205c2-196">有关详细信息，请参阅[Unity 物理学最佳实践](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="205c2-196">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="205c2-197">**效果**</span><span class="sxs-lookup"><span data-stu-id="205c2-197">**Animations**</span></span>

    <span data-ttu-id="205c2-198">禁用 Animator 组件禁用空闲动画（禁用游戏对象不会产生相同的效果）。</span><span class="sxs-lookup"><span data-stu-id="205c2-198">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="205c2-199">避免 animator 所在的设计模式将值设置为相同的值。</span><span class="sxs-lookup"><span data-stu-id="205c2-199">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="205c2-200">此方法会产生相当大的开销，对应用程序没有影响。</span><span class="sxs-lookup"><span data-stu-id="205c2-200">There is considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="205c2-201">在此处了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="205c2-201">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="205c2-202">**复杂算法**</span><span class="sxs-lookup"><span data-stu-id="205c2-202">**Complex algorithms**</span></span>

    <span data-ttu-id="205c2-203">如果你的应用程序使用的是复杂的算法，如反向运动、路径查找等，查找更简单的方法或调整相关设置的性能</span><span class="sxs-lookup"><span data-stu-id="205c2-203">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="205c2-204">CPU 到 GPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="205c2-204">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="205c2-205">通常情况下，CPU 到 GPU 的性能会下降到提交到图形卡的**绘图调用**。</span><span class="sxs-lookup"><span data-stu-id="205c2-205">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="205c2-206">若要提高性能，需要以战略**a 的**方式绘制调用，或将其作为最佳结果**重构**。</span><span class="sxs-lookup"><span data-stu-id="205c2-206">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="205c2-207">由于绘图调用本身会消耗大量资源，因此减少它们会减少所需的全部工作。</span><span class="sxs-lookup"><span data-stu-id="205c2-207">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="205c2-208">此外，在绘图调用之间进行的状态更改需要在图形驱动程序中执行昂贵的验证和翻译步骤，因此，重新构建应用程序的绘图调用以限制状态更改（即</span><span class="sxs-lookup"><span data-stu-id="205c2-208">Further, state changes between draw calls requires costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes(i.e</span></span> <span data-ttu-id="205c2-209">不同的资料等）可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="205c2-209">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="205c2-210">Unity 提供了一个很好的文章，为其平台的批处理绘图调用提供了概述和深入。</span><span class="sxs-lookup"><span data-stu-id="205c2-210">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="205c2-211">Unity 绘图调用批处理</span><span class="sxs-lookup"><span data-stu-id="205c2-211">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="205c2-212">单次传递实例呈现</span><span class="sxs-lookup"><span data-stu-id="205c2-212">Single pass instanced rendering</span></span>

<span data-ttu-id="205c2-213">Unity 中的单个 Pass 实例呈现允许每个眼睛的绘图调用缩小到一个实例绘图调用。</span><span class="sxs-lookup"><span data-stu-id="205c2-213">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="205c2-214">由于两次绘图调用之间的缓存一致性，因此也会对 GPU 进行一些性能改进。</span><span class="sxs-lookup"><span data-stu-id="205c2-214">Due to cache coherency between two draw calls, there is also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="205c2-215">在 Unity 项目中启用此功能</span><span class="sxs-lookup"><span data-stu-id="205c2-215">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="205c2-216">打开**播放机 XR 设置**（ > **Player** > "**设置**" "**编辑**" > **项目设置**</span><span class="sxs-lookup"><span data-stu-id="205c2-216">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="205c2-217">从 "**立体声呈现方法**" 下拉菜单中选择 "**单一传递实例**" （必须选中 "**支持虚拟现实**" 复选框）</span><span class="sxs-lookup"><span data-stu-id="205c2-217">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="205c2-218">有关此呈现方法的详细信息，请阅读有关 Unity 的以下文章。</span><span class="sxs-lookup"><span data-stu-id="205c2-218">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="205c2-219">如何通过高级立体声呈现最大化 AR 和 VR 性能</span><span class="sxs-lookup"><span data-stu-id="205c2-219">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="205c2-220">单步实例</span><span class="sxs-lookup"><span data-stu-id="205c2-220">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="205c2-221">如果开发人员已有未为实例化编写的现有自定义着色器，则会出现单一传递实例呈现的一个常见问题。</span><span class="sxs-lookup"><span data-stu-id="205c2-221">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="205c2-222">启用此功能后，开发人员可能会注意到某些 Gameobject 只会在一眼中呈现。</span><span class="sxs-lookup"><span data-stu-id="205c2-222">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="205c2-223">这是因为关联的自定义着色器没有用于实例化的适当属性。</span><span class="sxs-lookup"><span data-stu-id="205c2-223">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="205c2-224">有关如何解决此问题的详细说明，请参阅针对基于 Unity 的[HoloLens 的单一传递立体声呈现](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)</span><span class="sxs-lookup"><span data-stu-id="205c2-224">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="205c2-225">静态批处理</span><span class="sxs-lookup"><span data-stu-id="205c2-225">Static batching</span></span>

<span data-ttu-id="205c2-226">Unity 能够批处理多个静态对象，以减少对 GPU 的调用。</span><span class="sxs-lookup"><span data-stu-id="205c2-226">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="205c2-227">静态批处理适用于 Unity 中的大多数[呈现](https://docs.unity3d.com/ScriptReference/Renderer.html)器对象**1）共享相同的材料**， **2）全部标记为\*静态**\* （选择 Unity 中的对象，然后单击检查器右上方的复选框）。</span><span class="sxs-lookup"><span data-stu-id="205c2-227">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and click the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="205c2-228">不能在应用程序的运行时中移动标记为*静态*的 gameobject。</span><span class="sxs-lookup"><span data-stu-id="205c2-228">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="205c2-229">因此，静态批处理可能难以在 HoloLens 上利用，几乎每个对象都需要放置、移动、缩放等。对于沉浸式耳机，静态批处理可以显著减少绘图调用，从而提高性能。</span><span class="sxs-lookup"><span data-stu-id="205c2-229">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="205c2-230">有关更多详细信息，请参阅[Unity 中的绘图调用批处理中](https://docs.unity3d.com/Manual/DrawCallBatching.html)的*静态批处理*。</span><span class="sxs-lookup"><span data-stu-id="205c2-230">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="205c2-231">动态批处理</span><span class="sxs-lookup"><span data-stu-id="205c2-231">Dynamic batching</span></span>

<span data-ttu-id="205c2-232">由于将对象标记为适用于 HoloLens 开发的*静态*对象是有问题的，因此动态批处理可以很好地用于补偿此缺少的功能。</span><span class="sxs-lookup"><span data-stu-id="205c2-232">Since it is problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="205c2-233">当然，它也可用于沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="205c2-233">Of course, it is can also be useful on immersive headsets as well.</span></span> <span data-ttu-id="205c2-234">如果启用 Unity 中的动态批处理，则可能会很难，因为 Gameobject 必须**是）共享相同的材料**和**b），以满足较长的其他标准列表**。</span><span class="sxs-lookup"><span data-stu-id="205c2-234">Dynamic batching in Unity can be difficult though to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="205c2-235">有关完整列表，请参阅在[Unity 中的绘图调用批处理中](https://docs.unity3d.com/Manual/DrawCallBatching.html)的*动态批处理*。</span><span class="sxs-lookup"><span data-stu-id="205c2-235">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="205c2-236">最常见的情况是，Gameobject 因为关联的网格数据不能超过300个顶点而变为无效。</span><span class="sxs-lookup"><span data-stu-id="205c2-236">Most commonly, GameObjects become invalid to be batched dynamically because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="205c2-237">其他技术</span><span class="sxs-lookup"><span data-stu-id="205c2-237">Other techniques</span></span>

<span data-ttu-id="205c2-238">仅当多个 Gameobject 可以共享同一材料时才会进行批处理。</span><span class="sxs-lookup"><span data-stu-id="205c2-238">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="205c2-239">通常，这将被阻止 Gameobject 对其各自的材料具有独特的纹理。</span><span class="sxs-lookup"><span data-stu-id="205c2-239">Typically this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="205c2-240">将纹理组合到一个大纹理（一种称为[纹理 Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)的方法）是很常见的。</span><span class="sxs-lookup"><span data-stu-id="205c2-240">It is common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="205c2-241">此外，更好的做法是，尽可能将网格合并到一个 GameObject 中。</span><span class="sxs-lookup"><span data-stu-id="205c2-241">Further, it is generally preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="205c2-242">Unity 中的每个呈现器都将具有关联的绘图调用，而不是在一个呈现器下提交组合网格。</span><span class="sxs-lookup"><span data-stu-id="205c2-242">Each Renderer in Unity will have it's associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span>

>[!NOTE]
> <span data-ttu-id="205c2-243">修改呈现器的属性时，在运行时将创建材料的副本，因此可能会破坏批处理。</span><span class="sxs-lookup"><span data-stu-id="205c2-243">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="205c2-244">使用 sharedMaterial 可跨 Gameobject 修改共享的材料属性。</span><span class="sxs-lookup"><span data-stu-id="205c2-244">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="205c2-245">GPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="205c2-245">GPU performance recommendations</span></span>

<span data-ttu-id="205c2-246">了解有关[优化 Unity 中的图形呈现的](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)详细信息</span><span class="sxs-lookup"><span data-stu-id="205c2-246">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span>

### <a name="optimize-depth-buffer-sharing"></a><span data-ttu-id="205c2-247">优化深度缓冲区共享</span><span class="sxs-lookup"><span data-stu-id="205c2-247">Optimize depth buffer sharing</span></span>

<span data-ttu-id="205c2-248">通常建议在**播放机 XR 设置**下启用**深度缓冲区共享**以优化[全息影像稳定性](Hologram-stability.md)。</span><span class="sxs-lookup"><span data-stu-id="205c2-248">It is generally recommended to enable **Depth buffer sharing** under **Player XR Settings** to optimize for [hologram stability](Hologram-stability.md).</span></span> <span data-ttu-id="205c2-249">但是，在使用此设置启用基于深度的后期 reprojection 时，建议选择**16 位深度格式**而不是**24 位深度格式**。</span><span class="sxs-lookup"><span data-stu-id="205c2-249">When enabling depth-based late-stage reprojection with this setting however, it is recommended to select **16-bit depth format** instead of **24-bit depth format**.</span></span> <span data-ttu-id="205c2-250">16位深度缓冲区会大幅降低与深度缓冲区通信关联的带宽（以及与电源相关的能力）。</span><span class="sxs-lookup"><span data-stu-id="205c2-250">The 16-bit depth buffers will drastically reduces the bandwidth (and thus power) associated with depth buffer traffic.</span></span> <span data-ttu-id="205c2-251">这可以是同时降低电源和性能的巨大优势。</span><span class="sxs-lookup"><span data-stu-id="205c2-251">This can be a big win both in power reduction and performance improvement.</span></span> <span data-ttu-id="205c2-252">但是，通过使用*16 位深度格式*可以产生两个可能的负面结果。</span><span class="sxs-lookup"><span data-stu-id="205c2-252">However, there are two possible negative outcomes by using *16-bit depth format*.</span></span>

<span data-ttu-id="205c2-253">**Z-反击**</span><span class="sxs-lookup"><span data-stu-id="205c2-253">**Z-Fighting**</span></span>

<span data-ttu-id="205c2-254">降低深度范围保真使比24位更有可能出现[z 反击](https://en.wikipedia.org/wiki/Z-fighting)。</span><span class="sxs-lookup"><span data-stu-id="205c2-254">The reduced depth range fidelity makes [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) more likely to occur with 16-bit than 24-bit.</span></span> <span data-ttu-id="205c2-255">若要避免这些项目，请修改[Unity 相机](https://docs.unity3d.com/Manual/class-Camera.html)的 "近处/远处" 剪辑平面以降低精度。</span><span class="sxs-lookup"><span data-stu-id="205c2-255">To avoid these artifacts, modify the near/far clip planes of the [Unity camera](https://docs.unity3d.com/Manual/class-Camera.html) to account for the lower precision.</span></span> <span data-ttu-id="205c2-256">对于基于 HoloLens 的应用程序，50m （而不是 Unity 的默认1000m）的 far 剪裁平面通常可以消除任何 z 反击。</span><span class="sxs-lookup"><span data-stu-id="205c2-256">For HoloLens-based applications, a far clip plane of 50m instead of the Unity default 1000m can generally eliminate any z-fighting.</span></span>

<span data-ttu-id="205c2-257">**禁用的模具缓冲区**</span><span class="sxs-lookup"><span data-stu-id="205c2-257">**Disabled Stencil Buffer**</span></span>

<span data-ttu-id="205c2-258">当 Unity 创建[具有16位深度的着色纹理](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)时，不会创建任何模具缓冲区。</span><span class="sxs-lookup"><span data-stu-id="205c2-258">When Unity creates a [Render Texture with 16-bit depth](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), there is no stencil buffer created.</span></span> <span data-ttu-id="205c2-259">选择24位深度格式后，每个 Unity 文档将创建一个24位 z 缓冲区和一个[8 位的模具缓冲区](https://docs.unity3d.com/Manual/SL-Stencil.html)（如果32位适用于通常情况下的设备，如 HoloLens）。</span><span class="sxs-lookup"><span data-stu-id="205c2-259">Selecting 24-bit depth format, per Unity documentation, will create a 24-bit z-buffer as well as an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html) (if 32-bit is applicable on device which is generally the case such as HoloLens).</span></span>

### <a name="avoid-full-screen-effects"></a><span data-ttu-id="205c2-260">避免全屏效果</span><span class="sxs-lookup"><span data-stu-id="205c2-260">Avoid full-screen effects</span></span>

<span data-ttu-id="205c2-261">在全屏幕上操作的方法可能相当昂贵，因为它们的数量级顺序是每个帧的数百万个操作。</span><span class="sxs-lookup"><span data-stu-id="205c2-261">Techniques that operate on the full screen can be quite expensive since their order of magnitude is millions of operations every frame.</span></span> <span data-ttu-id="205c2-262">因此，建议避免使用[后期处理效果](https://docs.unity3d.com/Manual/PostProcessingOverview.html)，如抗锯齿、布隆等。</span><span class="sxs-lookup"><span data-stu-id="205c2-262">Thus, it is recommended to avoid [post-processing effects](https://docs.unity3d.com/Manual/PostProcessingOverview.html) such as anti-aliasing, bloom, and more.</span></span>

### <a name="optimal-lighting-settings"></a><span data-ttu-id="205c2-263">最佳照明设置</span><span class="sxs-lookup"><span data-stu-id="205c2-263">Optimal lighting settings</span></span>

<span data-ttu-id="205c2-264">Unity 中的[实时全局照明](https://docs.unity3d.com/Manual/GIIntro.html)可提供数量的视觉效果，但涉及到非常昂贵的照明计算。</span><span class="sxs-lookup"><span data-stu-id="205c2-264">[Real-time Global Illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide oustanding visual results but involves quite expensive lighting calculations.</span></span> <span data-ttu-id="205c2-265">建议通过**窗口** > **呈现**为每个 Unity 场景文件禁用实时全局照明 > **照明设置**> 取消选中 "**实时全局照明**"。</span><span class="sxs-lookup"><span data-stu-id="205c2-265">It is recommended to disable Realtime Global Illumination for every Unity scene file via **Window** > **Rendering** > **Lighting Settings** > Uncheck **Real-time Global Illumination**.</span></span>

<span data-ttu-id="205c2-266">此外，建议禁用所有阴影转换，因为这也会将昂贵的 GPU 传递添加到 Unity 场景。</span><span class="sxs-lookup"><span data-stu-id="205c2-266">Further, it is recommended to disable all shadow casting as these also add expensive GPU passes onto a Unity scene.</span></span> <span data-ttu-id="205c2-267">可以按光禁用阴影，但也可以通过质量设置对其进行控制整体。</span><span class="sxs-lookup"><span data-stu-id="205c2-267">Shadows can be disable per light but can also be controlled holistically via Quality settings.</span></span>

<span data-ttu-id="205c2-268">**编辑** > **项目设置**，然后选择 "**质量**" 类别 > 为 UWP 平台选择**低质量**。</span><span class="sxs-lookup"><span data-stu-id="205c2-268">**Edit** > **Project Settings**, then select the **Quality** category > Select **Low Quality** for the UWP Platform.</span></span> <span data-ttu-id="205c2-269">还可以仅设置**shadows**属性来**禁用阴影**。</span><span class="sxs-lookup"><span data-stu-id="205c2-269">One can also just set the **Shadows** property to **Disable Shadows**.</span></span>

### <a name="reduce-poly-count"></a><span data-ttu-id="205c2-270">减少 poly 计数</span><span class="sxs-lookup"><span data-stu-id="205c2-270">Reduce poly count</span></span>

<span data-ttu-id="205c2-271">多边形计数通常通过</span><span class="sxs-lookup"><span data-stu-id="205c2-271">Polygon count is usually reduced by either</span></span>
1) <span data-ttu-id="205c2-272">从场景中删除对象</span><span class="sxs-lookup"><span data-stu-id="205c2-272">Removing objects from a scene</span></span>
2) <span data-ttu-id="205c2-273">降低给定网格的多边形数的资产 decimation</span><span class="sxs-lookup"><span data-stu-id="205c2-273">Asset decimation which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="205c2-274">在应用程序中实现[级别的详细信息（LOD）系统](https://docs.unity3d.com/Manual/LevelOfDetail.html)，该系统将呈现远离相同几何图形的较小多边形版本的对象</span><span class="sxs-lookup"><span data-stu-id="205c2-274">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application which renders far away objects with lower-polygon version of the same geometry</span></span>

### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="205c2-275">了解 Unity 中的着色器</span><span class="sxs-lookup"><span data-stu-id="205c2-275">Understanding shaders in Unity</span></span>

<span data-ttu-id="205c2-276">比较性能着色器的简单近似值是确定每个运行时执行的平均操作数。</span><span class="sxs-lookup"><span data-stu-id="205c2-276">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="205c2-277">可在 Unity 中轻松完成此操作。</span><span class="sxs-lookup"><span data-stu-id="205c2-277">This can be done easily in Unity.</span></span>

1) <span data-ttu-id="205c2-278">选择着色器资产或选择材料，然后在检查器窗口的右上角选择齿轮图标，然后选择 **"选择着色器"**</span><span class="sxs-lookup"><span data-stu-id="205c2-278">Select your shader asset or select a material, then in top right corner of the inspector window, select the gear icon and then **"Select Shader"**</span></span>

    ![选择 Unity 中的着色器](images/Select-shader-unity.png)
2) <span data-ttu-id="205c2-280">选择着色器资产后，单击 "检查器" 窗口下的 **"编译并显示代码"** 按钮</span><span class="sxs-lookup"><span data-stu-id="205c2-280">With the shader asset selected, click the **"Compile and show code"** button under the inspector window</span></span>

    ![在 Unity 中编译着色器代码](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="205c2-282">编译完成后，查找结果中的 "统计信息" 部分，其中包含用于顶点着色器和像素着色器的不同操作（注意：像素着色器通常也称为片段着色器）</span><span class="sxs-lookup"><span data-stu-id="205c2-282">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity 标准着色器操作](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a><span data-ttu-id="205c2-284">优化像素着色器</span><span class="sxs-lookup"><span data-stu-id="205c2-284">Optmize pixel shaders</span></span>

<span data-ttu-id="205c2-285">使用上述方法查看编译的统计信息结果，[片段着色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)通常执行的操作比平均[顶点着色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)要多。</span><span class="sxs-lookup"><span data-stu-id="205c2-285">Looking at the compiled statistic results using the method above, the [fragment shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) will generally execute more operations than the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) on average.</span></span> <span data-ttu-id="205c2-286">片段着色器（也称为像素着色器）在屏幕输出上按像素执行，而顶点着色器仅对绘制到屏幕的所有网格的每个顶点执行。</span><span class="sxs-lookup"><span data-stu-id="205c2-286">The fragment shader, also known as the pixel shader, is executed per pixel on the screen output while the vertex shader is only executed per-vertex of all meshes being drawn to the screen.</span></span> 

<span data-ttu-id="205c2-287">因此，与顶点着色器相比，不仅仅是由于所有照明计算，片段着色器都有更多的说明，碎片着色器几乎总是在较大的数据集上执行。</span><span class="sxs-lookup"><span data-stu-id="205c2-287">Thus, not only do fragment shaders have more instructions than vertex shaders because of all the lighting calculations, fragment shaders are almost always executed on a larger dataset.</span></span> <span data-ttu-id="205c2-288">例如，如果屏幕输出为 2k x 2k，则片段着色器可以执行 2000 \* 2000 = 4000000 次。</span><span class="sxs-lookup"><span data-stu-id="205c2-288">For example, if the screen output is a 2k by 2k image, then the fragment shader can get executed 2,000\*2,000 = 4,000,000 times.</span></span> <span data-ttu-id="205c2-289">如果呈现两个眼睛，此数字会加倍，因为有两个屏幕。</span><span class="sxs-lookup"><span data-stu-id="205c2-289">If rendering two eyes, this number doubles since there are two screens.</span></span> <span data-ttu-id="205c2-290">如果混合现实应用程序具有多个传递、全屏后处理效果或将多个网格呈现到同一个像素，则此数字会大幅增加。</span><span class="sxs-lookup"><span data-stu-id="205c2-290">If a mixed reality application has multiple passes, full-screen post-processing effects, or rendering multiple meshes to the same pixel, this number will increase dramatically.</span></span> 

<span data-ttu-id="205c2-291">因此，在片段着色器中减少操作的数量通常可以比顶点着色器中的优化更好地提高性能。</span><span class="sxs-lookup"><span data-stu-id="205c2-291">Therefore, reducing the number of operations in the fragment shader can generally give far greater performance gains over optimizations in the vertex shader.</span></span>

#### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="205c2-292">Unity 标准着色器替代项</span><span class="sxs-lookup"><span data-stu-id="205c2-292">Unity Standard shader alternatives</span></span>

<span data-ttu-id="205c2-293">请不要使用基于物理的渲染（.PBR）或其他高质量的着色器，而是了解如何利用更高性能和更便宜的着色器。</span><span class="sxs-lookup"><span data-stu-id="205c2-293">Instead of using a physically based rendering (PBR) or other high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="205c2-294">[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供了已针对混合现实项目进行优化的[MRTK 标准着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)。</span><span class="sxs-lookup"><span data-stu-id="205c2-294">The [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides the [MRTK standard shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="205c2-295">与 Unity 标准着色器相比，Unity 还提供了 unlit、顶点发亮、漫射以及其他简化的着色器选项。</span><span class="sxs-lookup"><span data-stu-id="205c2-295">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are significantly faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="205c2-296">有关更多详细信息，请参阅[内置着色器的使用情况和性能](https://docs.unity3d.com/Manual/shader-Performance.html)。</span><span class="sxs-lookup"><span data-stu-id="205c2-296">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

#### <a name="shader-preloading"></a><span data-ttu-id="205c2-297">着色器预加载</span><span class="sxs-lookup"><span data-stu-id="205c2-297">Shader preloading</span></span>

<span data-ttu-id="205c2-298">使用*着色器预加载*和其他技巧优化[着色器的加载时间](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)。</span><span class="sxs-lookup"><span data-stu-id="205c2-298">Use *Shader preloading* and other tricks to optimize [shader load time](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html).</span></span> <span data-ttu-id="205c2-299">特别是，着色器预加载意味着你不会看到任何 hitches，因为运行时着色器编译。</span><span class="sxs-lookup"><span data-stu-id="205c2-299">In particular, shader preloading means you won't see any hitches due to runtime shader compilation.</span></span>

### <a name="limit-overdraw"></a><span data-ttu-id="205c2-300">限制过度绘制</span><span class="sxs-lookup"><span data-stu-id="205c2-300">Limit overdraw</span></span>

<span data-ttu-id="205c2-301">在 Unity 中，可以通过在**场景视图**的左上角切换 "[**绘图模式" 菜单**](https://docs.unity3d.com/Manual/ViewModes.html)并选择 "**过度绘制**"，为其场景显示过度绘制。</span><span class="sxs-lookup"><span data-stu-id="205c2-301">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="205c2-302">通常，在将对象发送到 GPU 之前提前剔除对象，可减轻过度绘制。</span><span class="sxs-lookup"><span data-stu-id="205c2-302">Generally, overdraw can be mitigated by culling objects ahead of time before they are sent to the GPU.</span></span> <span data-ttu-id="205c2-303">Unity 提供了有关为其引擎实现[封闭剔除](https://docs.unity3d.com/Manual/OcclusionCulling.html)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="205c2-303">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="205c2-304">内存建议</span><span class="sxs-lookup"><span data-stu-id="205c2-304">Memory recommendations</span></span>

<span data-ttu-id="205c2-305">内存分配过多 & 释放操作可能对全息应用程序产生不利影响，从而导致性能不一致、冻结帧和其他不利行为。</span><span class="sxs-lookup"><span data-stu-id="205c2-305">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="205c2-306">在 Unity 中进行开发时，了解内存的注意事项尤其重要，因为内存管理由垃圾回收器控制。</span><span class="sxs-lookup"><span data-stu-id="205c2-306">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="205c2-307">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="205c2-307">Garbage collection</span></span>

<span data-ttu-id="205c2-308">激活 GC 时，全息应用会将计算时间松散地处理到垃圾回收器（GC），以分析在执行期间不再处于范围内的对象，从而使其可供重复使用。</span><span class="sxs-lookup"><span data-stu-id="205c2-308">Holographic apps will loose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released so it can be made available for re-use.</span></span> <span data-ttu-id="205c2-309">常数分配和取消分配通常需要垃圾回收器才能更频繁地运行，从而影响性能和用户体验。</span><span class="sxs-lookup"><span data-stu-id="205c2-309">Constant allocations and de-allocations will generally require the garbage collector to run more frequently thus hurting performance and user experience.</span></span>

<span data-ttu-id="205c2-310">Unity 提供了一个很好的页面，其中详细说明了垃圾回收器的工作方式，以及如何编写更高效的代码来处理内存管理。</span><span class="sxs-lookup"><span data-stu-id="205c2-310">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="205c2-311">优化 Unity 游戏中的垃圾回收</span><span class="sxs-lookup"><span data-stu-id="205c2-311">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="205c2-312">导致过多垃圾回收的最常见做法之一是不会缓存对 Unity 开发中的组件和类的引用。</span><span class="sxs-lookup"><span data-stu-id="205c2-312">One of the most common practices that leads to excessive garbage collection is not caching references to components and classes in Unity development.</span></span> <span data-ttu-id="205c2-313">任何引用都应在开始（）或唤醒（）期间捕获，并在后续函数（如 Update （）或 Behaviour （））中重新使用。</span><span class="sxs-lookup"><span data-stu-id="205c2-313">Any references should be captured during Start() or Awake() and re-used in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="205c2-314">其他快速提示：</span><span class="sxs-lookup"><span data-stu-id="205c2-314">Other quick tips:</span></span>
- <span data-ttu-id="205c2-315">使用[StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C#类在运行时动态生成复杂字符串</span><span class="sxs-lookup"><span data-stu-id="205c2-315">Use the [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="205c2-316">当不再需要 Log （）时，请将其删除，因为它们仍在应用的所有内部版本中执行</span><span class="sxs-lookup"><span data-stu-id="205c2-316">Remove calls to Debug.Log() when no longer needed as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="205c2-317">如果您的全息应用程序通常需要大量内存，请考虑在加载阶段（例如，在呈现加载或转换屏幕时[ _**）调用 system.web**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) 。</span><span class="sxs-lookup"><span data-stu-id="205c2-317">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="205c2-318">对象池</span><span class="sxs-lookup"><span data-stu-id="205c2-318">Object pooling</span></span>

<span data-ttu-id="205c2-319">对象池是一种常用技术，可降低对象 & 释放的持续分配成本。</span><span class="sxs-lookup"><span data-stu-id="205c2-319">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="205c2-320">这是通过以下方式实现的：分配一个较大的相同对象池，并重新使用此池中的非活动可用实例，而不是随着时间推移不断地生成和销毁对象。</span><span class="sxs-lookup"><span data-stu-id="205c2-320">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="205c2-321">对象池非常适合在应用过程中具有可变生存期的重复使用的组件。</span><span class="sxs-lookup"><span data-stu-id="205c2-321">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="205c2-322">Unity 中的对象池教程</span><span class="sxs-lookup"><span data-stu-id="205c2-322">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="205c2-323">启动性能</span><span class="sxs-lookup"><span data-stu-id="205c2-323">Startup performance</span></span>

<span data-ttu-id="205c2-324">你应考虑使用较小的场景启动你的应用程序，然后使用 *[SceneManager](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 加载场景的其余部分。</span><span class="sxs-lookup"><span data-stu-id="205c2-324">You should consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="205c2-325">这允许你的应用程序尽可能快地进入交互状态。</span><span class="sxs-lookup"><span data-stu-id="205c2-325">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="205c2-326">请注意，当新场景正在激活并且任何呈现的内容可能断断续续或不便时，可能会出现较大的 CPU 峰值。</span><span class="sxs-lookup"><span data-stu-id="205c2-326">Be aware that there may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="205c2-327">解决这种情况的一种方法是，在要加载的场景上将 AsyncOperation. allowSceneActivation 属性设置为 false，等待场景加载，将屏幕清除为黑色，然后将其重新设置为 true 以完成场景激活。</span><span class="sxs-lookup"><span data-stu-id="205c2-327">One way to work around this is to set the AsyncOperation.allowSceneActivation property to false on the scene being loaded, wait for the scene to load, clear the screen to black, and then set back to true to complete the scene activation.</span></span>

<span data-ttu-id="205c2-328">请记住，当启动场景正在加载时，将向用户显示全息的初始屏幕。</span><span class="sxs-lookup"><span data-stu-id="205c2-328">Remember that while the startup scene is loading the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="205c2-329">另请参阅</span><span class="sxs-lookup"><span data-stu-id="205c2-329">See also</span></span>
- [<span data-ttu-id="205c2-330">优化 Unity 游戏中的图形呈现</span><span class="sxs-lookup"><span data-stu-id="205c2-330">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="205c2-331">优化 Unity 游戏中的垃圾回收</span><span class="sxs-lookup"><span data-stu-id="205c2-331">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="205c2-332">[物理学最佳实践 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="205c2-332">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="205c2-333">[优化脚本 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="205c2-333">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>
