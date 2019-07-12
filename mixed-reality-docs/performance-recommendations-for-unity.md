---
title: Unity 的性能建议
description: 若要提高性能与混合的现实应用程序的特定于 unity 的提示。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 图形，cpu、 gpu 呈现，垃圾回收 hololens
ms.openlocfilehash: b0821f07184bff8630f6b6af0d0fc461f6fcd133
ms.sourcegitcommit: 8f3ff9738397d9b9fdf4703b14b89d416f0186a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2019
ms.locfileid: "67843337"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="3e228-104">Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="3e228-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="3e228-105">本文基于讨论中所述[混合现实的性能建议](understanding-performance-for-mixed-reality.md)但重点介绍特定于 Unity 引擎环境的知识。</span><span class="sxs-lookup"><span data-stu-id="3e228-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unity engine environment.</span></span>

<span data-ttu-id="3e228-106">此外，还强烈建议开发人员检查[推荐的环境设置为 Unity 项目](Recommended-settings-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="3e228-106">It is also highly advisable that developers review the [recommended environment settings for Unity article](Recommended-settings-for-unity.md).</span></span> <span data-ttu-id="3e228-107">本文提供在构建混合现实应用程序的高性能方面的一些最重要的场景配置的内容。</span><span class="sxs-lookup"><span data-stu-id="3e228-107">This article has content with some of the most important scene configurations in regards to building performant Mixed Reality apps.</span></span> <span data-ttu-id="3e228-108">其中的某些建议设置是将突出显示如下。</span><span class="sxs-lookup"><span data-stu-id="3e228-108">Some of these recommended settings are highlighted below as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="3e228-109">如何使用 Unity 的配置文件</span><span class="sxs-lookup"><span data-stu-id="3e228-109">How to profile with Unity</span></span>

<span data-ttu-id="3e228-110">Unity 提供了 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** 内置这是一个不错的资源，以便收集有价值的性能见解为特定应用。</span><span class="sxs-lookup"><span data-stu-id="3e228-110">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="3e228-111">尽管一个可以运行在编辑器探查器，但这些度量值不表示 true 的运行时环境，因此，应谨慎使用此结果。</span><span class="sxs-lookup"><span data-stu-id="3e228-111">Although one can run the profiler in-editor, these metrics do not represent the true runtime environment and thus, results from this should be used cautiously.</span></span> <span data-ttu-id="3e228-112">建议为远程配置文件正在最准确和可操作见解的设备上运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="3e228-112">It is recommended to remotely profile your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="3e228-113">进一步来说，Unity[帧调试器](https://docs.unity3d.com/Manual/FrameDebugger.html)也是非常强大和见解工具使用。</span><span class="sxs-lookup"><span data-stu-id="3e228-113">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)  is also a very powerful and insight tool to utilize.</span></span>

<span data-ttu-id="3e228-114">Unity 提供了有关的很多文档：</span><span class="sxs-lookup"><span data-stu-id="3e228-114">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="3e228-115">如何连接[Unity 探查器附加到 UWP 应用程序远程](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span><span class="sxs-lookup"><span data-stu-id="3e228-115">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="3e228-116">如何有效地[诊断 Unity Profiler 的性能问题](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span><span class="sxs-lookup"><span data-stu-id="3e228-116">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="3e228-117">使用连接 Unity Profiler 及添加 GPU 探查器 (请参阅*添加 Profiler*中右上角)，所花费的时间在 CPU 和 GPU 上分别中间探查器，可以看到。</span><span class="sxs-lookup"><span data-stu-id="3e228-117">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="3e228-118">这允许开发人员进行快速估算，如果其应用程序是 CPU 还是 GPU 绑定。</span><span class="sxs-lookup"><span data-stu-id="3e228-118">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU vs GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="3e228-120">CPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="3e228-120">CPU performance recommendations</span></span>

<span data-ttu-id="3e228-121">以下内容介绍了更多的详尽性能做法，尤其是有针对性的 Unity （& a)C#开发。</span><span class="sxs-lookup"><span data-stu-id="3e228-121">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="3e228-122">缓存的引用</span><span class="sxs-lookup"><span data-stu-id="3e228-122">Cache references</span></span>

<span data-ttu-id="3e228-123">它是最佳做法是对所有相关的组件和 GameObjects 在初始化时的缓存引用。</span><span class="sxs-lookup"><span data-stu-id="3e228-123">It is best practice to cache references to all relevant components and GameObjects at initialization.</span></span> <span data-ttu-id="3e228-124">这是因为重复函数调用，如 *[GetComponent\<T > （)](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 是贵很多相对成本来存储指针的内存。</span><span class="sxs-lookup"><span data-stu-id="3e228-124">This is because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* are significantly more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="3e228-125">这也为适用于非常，定期用[Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)。</span><span class="sxs-lookup"><span data-stu-id="3e228-125">This also applies to to the very, regularly used [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).</span></span> <span data-ttu-id="3e228-126">*Camera.main*实际上就是使用 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* 越搜索具有的照相机对象在场景图的下方 *"MainCamera"* 标记。</span><span class="sxs-lookup"><span data-stu-id="3e228-126">*Camera.main* actually just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

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
> <span data-ttu-id="3e228-127">Avoid GetComponent(string)</span><span class="sxs-lookup"><span data-stu-id="3e228-127">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="3e228-128">使用时 *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* ，有少量的不同的重载。</span><span class="sxs-lookup"><span data-stu-id="3e228-128">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="3e228-129">请务必始终使用基于的类型实现，而绝不会基于字符串的搜索重载。</span><span class="sxs-lookup"><span data-stu-id="3e228-129">It is important to always use the Type based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="3e228-130">搜索由您的场景中的字符串是明显比搜索由类型成本更高。</span><span class="sxs-lookup"><span data-stu-id="3e228-130">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="3e228-131">（好）组件 GetComponent （类型）</span><span class="sxs-lookup"><span data-stu-id="3e228-131">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="3e228-132">（好）T GetComponent\<T > （)</span><span class="sxs-lookup"><span data-stu-id="3e228-132">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="3e228-133">（错误）组件 GetComponent(string) ></span><span class="sxs-lookup"><span data-stu-id="3e228-133">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="3e228-134">避免成本高昂的操作</span><span class="sxs-lookup"><span data-stu-id="3e228-134">Avoid expensive operations</span></span>

1) <span data-ttu-id="3e228-135">**避免使用[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span><span class="sxs-lookup"><span data-stu-id="3e228-135">**Avoid use of [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="3e228-136">尽管 LINQ 可以非常干净且轻松地读取和写入，但它通常需要更多的计算和特别详细内存分配比手动写出的算法。</span><span class="sxs-lookup"><span data-stu-id="3e228-136">Although LINQ can be very clean and easy to read and write, it generally requires much more computation and particularly more memory allocation than writing the algorithm out manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="3e228-137">**常见的 Unity Api**</span><span class="sxs-lookup"><span data-stu-id="3e228-137">**Common Unity APIs**</span></span>

    <span data-ttu-id="3e228-138">某些 Unity Api，虽然有用，可以执行代价很高。</span><span class="sxs-lookup"><span data-stu-id="3e228-138">Certain Unity APIs, although useful, can be very expensive to execute.</span></span> <span data-ttu-id="3e228-139">这些大部分涉及搜索整个场景图形的 GameObjects 一些匹配列表。</span><span class="sxs-lookup"><span data-stu-id="3e228-139">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="3e228-140">这些操作通常可以避免缓存引用或实现的相关 Gameobject 来跟踪在运行时引用管理器组件。</span><span class="sxs-lookup"><span data-stu-id="3e228-140">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects in question to track the references at runtime.</span></span>

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> <span data-ttu-id="3e228-141">*[Sendmessage （)](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 并 *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 应消除不惜一切代价。</span><span class="sxs-lookup"><span data-stu-id="3e228-141">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="3e228-142">这些函数可以是 1000 x 慢于直接函数调用的顺序。</span><span class="sxs-lookup"><span data-stu-id="3e228-142">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="3e228-143">**请注意装箱**</span><span class="sxs-lookup"><span data-stu-id="3e228-143">**Beware of boxing**</span></span>

    <span data-ttu-id="3e228-144">[装箱](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)是一个核心概念的C#语言和运行时。</span><span class="sxs-lookup"><span data-stu-id="3e228-144">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="3e228-145">它是值类型的变量，例如 char、 int、 bool 等包装到引用类型的变量的过程。</span><span class="sxs-lookup"><span data-stu-id="3e228-145">It is the process of wrapping value-typed variables such as char, int, bool, etc. into reference-typed variables.</span></span> <span data-ttu-id="3e228-146">值类型变量进行"装箱，"时包装内 System.Object 存储在托管堆上。</span><span class="sxs-lookup"><span data-stu-id="3e228-146">When a value-typed variable is "boxed", it is wrapped inside of a System.Object which is stored on the managed heap.</span></span> <span data-ttu-id="3e228-147">因此，分配内存和释放时，最终必须由垃圾回收器处理。</span><span class="sxs-lookup"><span data-stu-id="3e228-147">Thus, memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="3e228-148">这些分配和释放会产生性能开销和在许多情况下是不必要或可以轻松地替换为成本较低的替代方法。</span><span class="sxs-lookup"><span data-stu-id="3e228-148">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

#### <a name="repeating-code-paths"></a><span data-ttu-id="3e228-149">重复的代码路径</span><span class="sxs-lookup"><span data-stu-id="3e228-149">Repeating code paths</span></span>

<span data-ttu-id="3e228-150">任何重复的 Unity 回调函数 （即</span><span class="sxs-lookup"><span data-stu-id="3e228-150">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="3e228-151">更新） 每秒多次执行和/或应非常仔细地写入帧。</span><span class="sxs-lookup"><span data-stu-id="3e228-151">Update) that are executed many times per second and/or frame should be written very carefully.</span></span> <span data-ttu-id="3e228-152">任何成本高昂的操作会对性能产生巨大且一致的影响。</span><span class="sxs-lookup"><span data-stu-id="3e228-152">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="3e228-153">**空的回调函数**</span><span class="sxs-lookup"><span data-stu-id="3e228-153">**Empty callback functions**</span></span>

    <span data-ttu-id="3e228-154">虽然下面的代码可能看起来正常将应用程序，尤其是因为使用此代码块，每个 Unity 脚本自动初始化这些空回调可能实际上会变得非常昂贵。</span><span class="sxs-lookup"><span data-stu-id="3e228-154">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with this code block, these empty callbacks can actually become very expensive.</span></span> <span data-ttu-id="3e228-155">Unity 通过非托管/托管代码边界，UnityEngine 代码和应用程序代码之间进行往返操作。</span><span class="sxs-lookup"><span data-stu-id="3e228-155">Unity operates back and forth over an unmanaged/managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="3e228-156">即使没有要执行上下文切换此桥非常耗费资源。</span><span class="sxs-lookup"><span data-stu-id="3e228-156">Context switching over this bridge is fairly expensive even if there is nothing to execute.</span></span> <span data-ttu-id="3e228-157">这将成为你的应用有 100 个 Gameobject 组件具有空重复 Unity 回调的使用尤其存在问题。</span><span class="sxs-lookup"><span data-stu-id="3e228-157">This becomes especially problematic if your app has 100's of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="3e228-158">Update （） 是最常见的表现形式这种性能问题，但如下所示其他重复 Unity 回调可以是同样那么糟糕如果不更糟的是：FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span><span class="sxs-lookup"><span data-stu-id="3e228-158">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks such as the following can be equally as bad if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="3e228-159">**操作更看重运行一次每一帧**</span><span class="sxs-lookup"><span data-stu-id="3e228-159">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="3e228-160">以下的 Unity Api 都是很多全息版的应用程序的常见操作。</span><span class="sxs-lookup"><span data-stu-id="3e228-160">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="3e228-161">尽管不是始终可行，但这些函数的结果非常通常计算一次，结果重新利用给定的框架在应用程序。</span><span class="sxs-lookup"><span data-stu-id="3e228-161">Although not always possible, the results from these functions can very commonly be computed once and the results re-utilized across the application for a given frame.</span></span>

    <span data-ttu-id="3e228-162">a） 通常很好的做法具有专用的单一实例类或服务来处理你向场景的视线移动 Raycast，然后在所有其他场景组件，而不是使每个重复和实质上是相同 Raycast 操作重新使用此结果组件。</span><span class="sxs-lookup"><span data-stu-id="3e228-162">a) Generally it is good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then re-use this result in all other scene components, instead of making repeated and essentially identical Raycast operations by each component.</span></span> <span data-ttu-id="3e228-163">当然，某些应用程序可能需要从不同的源或针对不同的 raycasts [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)。</span><span class="sxs-lookup"><span data-stu-id="3e228-163">Of course, some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    <span data-ttu-id="3e228-164">b） 避免 GetComponent() 操作中重复的 Unity 回调，如通过 update （）[缓存引用](#cache-references)start （） 或 Awake() 中</span><span class="sxs-lookup"><span data-stu-id="3e228-164">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>

        UnityEngine.Object.GetComponent()

    <span data-ttu-id="3e228-165">c） 它是所有对象，如果可能，请在初始化和使用的实例都化的好办法[对象池](#object-pooling)回收并重复整个应用程序的运行时使用 GameObjects</span><span class="sxs-lookup"><span data-stu-id="3e228-165">c) It is good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and re-use GameObjects throughout runtime of your application</span></span>

        UnityEngine.Object.Instantiate()

3) <span data-ttu-id="3e228-166">**避免接口和虚拟构造**</span><span class="sxs-lookup"><span data-stu-id="3e228-166">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="3e228-167">调用函数调用通过接口与直接对象或调用虚函数通常情况下可以比使用直接构造或直接函数调用的昂贵得多。</span><span class="sxs-lookup"><span data-stu-id="3e228-167">Invoking function calls through interfaces vs direct objects or calling virtual functions can often times be much more expensive than utilizing direct constructs or direct function calls.</span></span> <span data-ttu-id="3e228-168">如果虚函数或接口为不必要的则应删除。</span><span class="sxs-lookup"><span data-stu-id="3e228-168">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="3e228-169">但是，性能下降的这些方法通常是值得进行权衡如果利用它们简化了开发协作、 代码的可读性，以及代码可维护性。</span><span class="sxs-lookup"><span data-stu-id="3e228-169">However, the performance hit for these approaches are generally worth the trade-off if utilizing them simplifies development collaboration, code readability, and code maintainability.</span></span> 

4) <span data-ttu-id="3e228-170">**避免通过值传递结构**</span><span class="sxs-lookup"><span data-stu-id="3e228-170">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="3e228-171">与类不同，结构是值类型，并直接传递到函数，其内容复制到新创建的实例。</span><span class="sxs-lookup"><span data-stu-id="3e228-171">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="3e228-172">此副本将添加的 CPU 开销以及在堆栈上的更多内存。</span><span class="sxs-lookup"><span data-stu-id="3e228-172">This copy adds CPU cost as well as additional memory on the stack.</span></span> <span data-ttu-id="3e228-173">对于小结构，其效果是通常很少，因此可接受。</span><span class="sxs-lookup"><span data-stu-id="3e228-173">For small structs, the effect is usually very minimal and thus acceptable.</span></span> <span data-ttu-id="3e228-174">但是，对于反复调用函数的每一帧以及函数采用较大的结构，如有可能修改要按引用传递的函数定义。</span><span class="sxs-lookup"><span data-stu-id="3e228-174">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="3e228-175">此处详细了解</span><span class="sxs-lookup"><span data-stu-id="3e228-175">Learn more here</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="3e228-176">其他</span><span class="sxs-lookup"><span data-stu-id="3e228-176">Miscellaneous</span></span>

1) <span data-ttu-id="3e228-177">**物理引擎**</span><span class="sxs-lookup"><span data-stu-id="3e228-177">**Physics**</span></span>

    <span data-ttu-id="3e228-178">a） 通常情况下，以提高物理引擎的最简单方法是时间的限制所用的物理或每秒的迭代次数量。</span><span class="sxs-lookup"><span data-stu-id="3e228-178">a) Generally, easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="3e228-179">当然，这将减少模拟准确性。</span><span class="sxs-lookup"><span data-stu-id="3e228-179">Of course, this will reduce simulation accuracy.</span></span> <span data-ttu-id="3e228-180">请参阅[TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) Unity 中</span><span class="sxs-lookup"><span data-stu-id="3e228-180">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="3e228-181">在 Unity 中的碰撞体 b） 该类型具有很大不同的性能特征。</span><span class="sxs-lookup"><span data-stu-id="3e228-181">b) The type of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="3e228-182">下面的顺序列出了大多数性能碰撞体到最高性能碰撞体从左到右。</span><span class="sxs-lookup"><span data-stu-id="3e228-182">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="3e228-183">它是最重要，以避免网格碰撞体是比基元碰撞体贵很多。</span><span class="sxs-lookup"><span data-stu-id="3e228-183">It is most important to avoid Mesh Colliders which are substantially more expensive than the primitive colliders.</span></span>

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    <span data-ttu-id="3e228-184">请参阅[Unity 物理最佳实践](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)的详细信息</span><span class="sxs-lookup"><span data-stu-id="3e228-184">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="3e228-185">**动画**</span><span class="sxs-lookup"><span data-stu-id="3e228-185">**Animations**</span></span>

    <span data-ttu-id="3e228-186">通过禁用动画器组件来禁用空闲的动画 （禁用游戏对象不会有相同的效果）。</span><span class="sxs-lookup"><span data-stu-id="3e228-186">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="3e228-187">避免设计模式，其中将动画器放置在一个循环将值设置为相同的操作。</span><span class="sxs-lookup"><span data-stu-id="3e228-187">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="3e228-188">没有增加大量开销，对于此技术，对应用程序没有影响。</span><span class="sxs-lookup"><span data-stu-id="3e228-188">There is considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="3e228-189">此处了解详情。</span><span class="sxs-lookup"><span data-stu-id="3e228-189">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="3e228-190">**复杂的算法**</span><span class="sxs-lookup"><span data-stu-id="3e228-190">**Complex algorithms**</span></span>

    <span data-ttu-id="3e228-191">如果你的应用程序使用反向运动学、 路径查找等复杂的算法，查找要查找更简单的方法或调整其性能的相关设置</span><span class="sxs-lookup"><span data-stu-id="3e228-191">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="3e228-192">CPU GPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="3e228-192">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="3e228-193">通常情况下，向下越高，CPU GPU 性能**绘图调用**提交到图形卡。</span><span class="sxs-lookup"><span data-stu-id="3e228-193">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="3e228-194">若要提高性能，绘图调用必须是多个巧妙布局**a） 减少**或**b） 重新构建**以获得最佳效果。</span><span class="sxs-lookup"><span data-stu-id="3e228-194">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="3e228-195">由于自身的绘图调用都是需要消耗大量资源，则减少它们将减少所需的整体工作。</span><span class="sxs-lookup"><span data-stu-id="3e228-195">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="3e228-196">此外，状态的绘图调用之间的更改需要成本高昂的验证和转换中的图形驱动程序的步骤，因此，重新构建的应用程序的绘图调用，以限制状态更改 （即</span><span class="sxs-lookup"><span data-stu-id="3e228-196">Further, state changes between draw calls requires costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes(i.e</span></span> <span data-ttu-id="3e228-197">不同的材料等） 可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="3e228-197">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="3e228-198">Unity 有一种很好的篇文章，概括介绍并深入探讨了批处理其平台的绘图调用。</span><span class="sxs-lookup"><span data-stu-id="3e228-198">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="3e228-199">Unity 绘制调用批处理</span><span class="sxs-lookup"><span data-stu-id="3e228-199">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="3e228-200">单个传递实例的呈现</span><span class="sxs-lookup"><span data-stu-id="3e228-200">Single pass instanced rendering</span></span>

<span data-ttu-id="3e228-201">在 Unity 中的单次传递 Instanced 呈现允许每只眼睛降低下一个实例化的绘图调用的绘图调用。</span><span class="sxs-lookup"><span data-stu-id="3e228-201">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="3e228-202">由于两个绘图调用之间的缓存一致性，还提供了一些性能改进以及在 GPU 上。</span><span class="sxs-lookup"><span data-stu-id="3e228-202">Due to cache coherency between two draw calls, there is also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="3e228-203">若要启用此功能在 Unity 项目中</span><span class="sxs-lookup"><span data-stu-id="3e228-203">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="3e228-204">打开**播放器 XR 设置**(转到**编辑** > **项目设置** > **播放机** > **XR 设置**)</span><span class="sxs-lookup"><span data-stu-id="3e228-204">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="3e228-205">选择**单个传递二次实例化**从**立体声呈现方法**下拉列表菜单 (**虚拟现实支持**必须选中复选框)</span><span class="sxs-lookup"><span data-stu-id="3e228-205">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="3e228-206">阅读以下文章 Unity 中使用此方法时呈现的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3e228-206">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="3e228-207">如何使用高级立体声呈现 AR 和 VR 性能最大化</span><span class="sxs-lookup"><span data-stu-id="3e228-207">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="3e228-208">单次传递实例化</span><span class="sxs-lookup"><span data-stu-id="3e228-208">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="3e228-209">如果开发人员已具有没有为编写的现有自定义着色器，会发生与单个传递实例呈现一个常见的问题实例化。</span><span class="sxs-lookup"><span data-stu-id="3e228-209">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="3e228-210">启用此功能后, 开发人员可能会注意到某些 GameObjects 仅呈现一眼中。</span><span class="sxs-lookup"><span data-stu-id="3e228-210">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="3e228-211">这是因为关联的自定义着色器不具有适当的属性为实例化。</span><span class="sxs-lookup"><span data-stu-id="3e228-211">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="3e228-212">请参阅[单个传递立体声的呈现 HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)从 Unity 如何解决此问题</span><span class="sxs-lookup"><span data-stu-id="3e228-212">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="3e228-213">静态批处理</span><span class="sxs-lookup"><span data-stu-id="3e228-213">Static batching</span></span>

<span data-ttu-id="3e228-214">Unity 是能够批处理多个静态对象，以减少到 GPU 的绘图调用。</span><span class="sxs-lookup"><span data-stu-id="3e228-214">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="3e228-215">静态批处理适用于大多数[呈现器](https://docs.unity3d.com/ScriptReference/Renderer.html)Unity 中的对象的**1） 共享同一种材料**并**2） 是所有标记为\*静态**\* (在 Unity 中选择一个对象，然后单击右上角的复选框右侧的检查器)。</span><span class="sxs-lookup"><span data-stu-id="3e228-215">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and click the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="3e228-216">标记为 GameObjects*静态*整个应用程序的运行时不能移动。</span><span class="sxs-lookup"><span data-stu-id="3e228-216">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="3e228-217">因此，静态批处理可能很难利用的 HoloLens 需要放置，已移动、 缩放等几乎每个对象上。对于沉浸式耳机，静态批处理可以显著减少的绘图调用并因此提高性能。</span><span class="sxs-lookup"><span data-stu-id="3e228-217">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="3e228-218">读取*静态批处理*下[绘制调用批处理在 Unity 中](https://docs.unity3d.com/Manual/DrawCallBatching.html)的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="3e228-218">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="3e228-219">动态批处理</span><span class="sxs-lookup"><span data-stu-id="3e228-219">Dynamic batching</span></span>

<span data-ttu-id="3e228-220">由于它是有问题，若要将对象标记为*静态*对于 HoloLens 开发动态批处理可以是一个强大的工具对此进行弥补缺少功能。</span><span class="sxs-lookup"><span data-stu-id="3e228-220">Since it is problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="3e228-221">当然，这是可以也十分有用也沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="3e228-221">Of course, it is can also be useful on immersive headsets as well.</span></span> <span data-ttu-id="3e228-222">在 Unity 中的动态批处理很难但若要启用，因为必须 GameObjects **a） 共享同一种材料**和**b） 满足其他条件一长串**。</span><span class="sxs-lookup"><span data-stu-id="3e228-222">Dynamic batching in Unity can be difficult though to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="3e228-223">读取*动态批处理*下[绘制调用批处理在 Unity 中](https://docs.unity3d.com/Manual/DrawCallBatching.html)的完整列表。</span><span class="sxs-lookup"><span data-stu-id="3e228-223">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="3e228-224">大多数情况下，GameObjects 变为无效，因为关联的网格数据可以是不能超过 300 顶点动态批处理。</span><span class="sxs-lookup"><span data-stu-id="3e228-224">Most commonly, GameObjects become invalid to be batched dynamically because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="3e228-225">其他技术</span><span class="sxs-lookup"><span data-stu-id="3e228-225">Other techniques</span></span>

<span data-ttu-id="3e228-226">如果多个 GameObjects 可以共享同一种材料，可以仅发生批处理。</span><span class="sxs-lookup"><span data-stu-id="3e228-226">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="3e228-227">通常这将阻止 GameObjects 若要为其各自的材料具有唯一的纹理的需求。</span><span class="sxs-lookup"><span data-stu-id="3e228-227">Typically this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="3e228-228">通常会将纹理组合成一个大的纹理，一种称为方法[纹理 Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)。</span><span class="sxs-lookup"><span data-stu-id="3e228-228">It is common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="3e228-229">此外，通常最好是将合并到一个 GameObject 的网格，可能和合理的位置。</span><span class="sxs-lookup"><span data-stu-id="3e228-229">Further, it is generally preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="3e228-230">在 Unity 中的每个呈现器会将其与提交下一个呈现器组合的网格的绘图调用相关联。</span><span class="sxs-lookup"><span data-stu-id="3e228-230">Each Renderer in Unity will have it's associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span> 

>[!NOTE]
> <span data-ttu-id="3e228-231">修改在运行时的 Renderer.material 属性将创建的材料的副本，并因此可能会中断批处理。</span><span class="sxs-lookup"><span data-stu-id="3e228-231">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="3e228-232">使用 Renderer.sharedMaterial 跨 GameObjects 修改共享的 material 属性。</span><span class="sxs-lookup"><span data-stu-id="3e228-232">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="3e228-233">GPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="3e228-233">GPU performance recommendations</span></span>

<span data-ttu-id="3e228-234">详细了解[优化在 Unity 中的图形呈现](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span><span class="sxs-lookup"><span data-stu-id="3e228-234">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span> 

### <a name="optimize-depth-buffer-sharing"></a><span data-ttu-id="3e228-235">优化深度缓冲区共享</span><span class="sxs-lookup"><span data-stu-id="3e228-235">Optimize depth buffer sharing</span></span>

<span data-ttu-id="3e228-236">通常建议以启用**深度缓冲区共享**下**播放器 XR 设置**优化[全息图稳定性](Hologram-stability.md)。</span><span class="sxs-lookup"><span data-stu-id="3e228-236">It is generally recommended to enable **Depth buffer sharing** under **Player XR Settings** to optimize for [hologram stability](Hologram-stability.md).</span></span> <span data-ttu-id="3e228-237">在启用此设置，但是使用基于深度的后期阶段 reprojection，建议选择**16 位深度格式**而不是**24 位深度格式**。</span><span class="sxs-lookup"><span data-stu-id="3e228-237">When enabling depth-based late-stage reprojection with this setting however, it is recommended to select **16-bit depth format** instead of **24-bit depth format**.</span></span> <span data-ttu-id="3e228-238">16 位深度缓冲区将极大地减少了带宽 （并因此电源） 深度缓冲区流量与相关联。</span><span class="sxs-lookup"><span data-stu-id="3e228-238">The 16-bit depth buffers will drastically reduces the bandwidth (and thus power) associated with depth buffer traffic.</span></span> <span data-ttu-id="3e228-239">这可以是一个强大的动力的优势，但仅适用于小型的深度范围作为经验[z 值争夺](https://en.wikipedia.org/wiki/Z-fighting)更有可能出现的 16 位比 24 位。</span><span class="sxs-lookup"><span data-stu-id="3e228-239">This can be a big power win, but is only applicable for experiences with a small depth range as [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) is more likely to occur with 16-bit than 24-bit.</span></span> <span data-ttu-id="3e228-240">若要避免这些项目，请修改的附近/远端剪裁平面[Unity 照相机](https://docs.unity3d.com/Manual/class-Camera.html)来应对较低的精度。</span><span class="sxs-lookup"><span data-stu-id="3e228-240">To avoid these artifacts, modify the near/far clip planes of the [Unity camera](https://docs.unity3d.com/Manual/class-Camera.html) to account for the lower precision.</span></span> <span data-ttu-id="3e228-241">对于基于 HoloLens 的应用程序，而不是 Unity 默认 1000 m 50 m 远端剪裁平面通常可以消除任何 z 值争夺。</span><span class="sxs-lookup"><span data-stu-id="3e228-241">For HoloLens-based applications, a far clip plane of 50m instead of the Unity default 1000m can generally eliminate any z-fighting.</span></span>

### <a name="reduce-poly-count"></a><span data-ttu-id="3e228-242">减少 poly 计数</span><span class="sxs-lookup"><span data-stu-id="3e228-242">Reduce poly count</span></span>

<span data-ttu-id="3e228-243">多边形计数通常会减少通过以下任一方法</span><span class="sxs-lookup"><span data-stu-id="3e228-243">Polygon count is usually reduced by either</span></span>
1) <span data-ttu-id="3e228-244">从一个场景中删除对象</span><span class="sxs-lookup"><span data-stu-id="3e228-244">Removing objects from a scene</span></span>
2) <span data-ttu-id="3e228-245">它可以减少为给定的网格的多边形资产抽取</span><span class="sxs-lookup"><span data-stu-id="3e228-245">Asset decimation which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="3e228-246">实现[的详细信息级别 (LOD) 系统](https://docs.unity3d.com/Manual/LevelOfDetail.html)到应用程序来呈现远而具有较低多边形版本的同一个几何对象</span><span class="sxs-lookup"><span data-stu-id="3e228-246">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application which renders far away objects with lower-polygon version of the same geometry</span></span>

### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="3e228-247">了解在 Unity 中的着色器</span><span class="sxs-lookup"><span data-stu-id="3e228-247">Understanding shaders in Unity</span></span>

<span data-ttu-id="3e228-248">轻松近似值进行比较的性能的着色器是确定每个操作的平均数目将在运行时执行。</span><span class="sxs-lookup"><span data-stu-id="3e228-248">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="3e228-249">这可以在 Unity 中轻松地实现。</span><span class="sxs-lookup"><span data-stu-id="3e228-249">This can be done easily in Unity.</span></span>

1) <span data-ttu-id="3e228-250">选择你的着色器资产或其他营销材料，然后在检查器窗口的右上角，选择齿轮图标，然后 **"选择着色器"**</span><span class="sxs-lookup"><span data-stu-id="3e228-250">Select your shader asset or select a material, then in top right corner of the inspector window, select the gear icon and then **"Select Shader"**</span></span>

    ![选择在 Unity 中的着色器](images/Select-shader-unity.png)
2) <span data-ttu-id="3e228-252">与所选着色器资产，请单击 **"编译和显示代码"** 按钮下的检查器窗口</span><span class="sxs-lookup"><span data-stu-id="3e228-252">With the shader asset selected, click the **"Compile and show code"** button under the inspector window</span></span>

    ![编译中 Unity 着色器代码](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="3e228-254">编译后，查看统计信息部分结果中的顶点和像素着色器为不同的操作数目 (注意： 像素着色器通常也称为片段着色器)</span><span class="sxs-lookup"><span data-stu-id="3e228-254">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity 标准着色器操作](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a><span data-ttu-id="3e228-256">优化像素着色器</span><span class="sxs-lookup"><span data-stu-id="3e228-256">Optmize pixel shaders</span></span>

<span data-ttu-id="3e228-257">查看使用上述方法的已编译统计信息结果[片段着色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)通常将执行更多操作比[顶点着色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)平均值。</span><span class="sxs-lookup"><span data-stu-id="3e228-257">Looking at the compiled statistic results using the method above, the [fragment shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) will generally execute more operations than the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) on average.</span></span> <span data-ttu-id="3e228-258">片段着色器，也称为像素着色器，每个像素输出仅执行每个顶点绘制到屏幕的所有网格的顶点着色器时在屏幕上执行。</span><span class="sxs-lookup"><span data-stu-id="3e228-258">The fragment shader, also known as the pixel shader, is executed per pixel on the screen output while the vertex shader is only executed per-vertex of all meshes being drawn to the screen.</span></span> 

<span data-ttu-id="3e228-259">因此，不仅片段着色器没有比顶点着色器的详细说明由于所有照明计算，几乎始终更大的数据集上执行片段着色器。</span><span class="sxs-lookup"><span data-stu-id="3e228-259">Thus, not only do fragment shaders have more instructions than vertex shaders because of all the lighting calculations, fragment shaders are almost always executed on a larger dataset.</span></span> <span data-ttu-id="3e228-260">例如，如果屏幕输出是由 2 个图像 2 k，然后片段着色器会得到 2，000 \* 2，000 = 4,000,000 执行一次时间。</span><span class="sxs-lookup"><span data-stu-id="3e228-260">For example, if the screen output is a 2k by 2k image, then the fragment shader can get executed 2,000\*2,000 = 4,000,000 times.</span></span> <span data-ttu-id="3e228-261">如果呈现两只眼睛，此数两倍，因为有两个屏幕。</span><span class="sxs-lookup"><span data-stu-id="3e228-261">If rendering two eyes, this number doubles since there are two screens.</span></span> <span data-ttu-id="3e228-262">如果混合的现实应用程序具有多个传递、 全屏后处理的效果，或呈现到同一像素的多个网格，此数值会显著增加。</span><span class="sxs-lookup"><span data-stu-id="3e228-262">If a mixed reality application has multiple passes, full-screen post-processing effects, or rendering multiple meshes to the same pixel, this number will increase dramatically.</span></span> 

<span data-ttu-id="3e228-263">因此，减少片段着色器中的操作的数量通常可以大得多的性能提升通过顶点着色器中的优化。</span><span class="sxs-lookup"><span data-stu-id="3e228-263">Therefore, reducing the number of operations in the fragment shader can generally give far greater performance gains over optimizations in the vertex shader.</span></span>

#### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="3e228-264">Unity 标准着色器替代项</span><span class="sxs-lookup"><span data-stu-id="3e228-264">Unity Standard shader alternatives</span></span>

<span data-ttu-id="3e228-265">而不是使用以物理方式根据的呈现 (PBR) 或其他高质量着色器，看看利用更高的性能和成本更低的着色器。</span><span class="sxs-lookup"><span data-stu-id="3e228-265">Instead of using a physically based rendering (PBR) or other high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="3e228-266">[混合现实 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供[MRTK 标准着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)已针对混合的现实项目进行优化的。</span><span class="sxs-lookup"><span data-stu-id="3e228-266">The [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides the [MRTK standard shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="3e228-267">Unity 也提供了向标准 Unity 着色器的不亮、 亮起顶点、 明显更快地进行比较的漫射，和其他简化着色器选项。</span><span class="sxs-lookup"><span data-stu-id="3e228-267">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are significantly faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="3e228-268">请参阅[使用情况和内置着色器性能](https://docs.unity3d.com/Manual/shader-Performance.html)更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="3e228-268">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

#### <a name="shader-preloading"></a><span data-ttu-id="3e228-269">预加载的着色器</span><span class="sxs-lookup"><span data-stu-id="3e228-269">Shader preloading</span></span>

<span data-ttu-id="3e228-270">使用*着色器预加载*和其他技巧来优化[着色器加载时间](http://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)。</span><span class="sxs-lookup"><span data-stu-id="3e228-270">Use *Shader preloading* and other tricks to optimize [shader load time](http://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html).</span></span> <span data-ttu-id="3e228-271">具体而言，预加载的着色器意味着不会看到任何虞由于运行时编译着色器。</span><span class="sxs-lookup"><span data-stu-id="3e228-271">In particular, shader preloading means you won't see any hitches due to runtime shader compilation.</span></span>

### <a name="limit-overdraw"></a><span data-ttu-id="3e228-272">限制过度绘制</span><span class="sxs-lookup"><span data-stu-id="3e228-272">Limit overdraw</span></span>

<span data-ttu-id="3e228-273">在 Unity 中，其中一个可以显示过度绘制为其场景中，通过切换[**绘图模式菜单**](https://docs.unity3d.com/Manual/ViewModes.html)中的左上角**场景视图**并选择**过度绘制**.</span><span class="sxs-lookup"><span data-stu-id="3e228-273">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="3e228-274">通常情况下，过度绘制可缓解通过剔除提前发送到 GPU 前的对象。</span><span class="sxs-lookup"><span data-stu-id="3e228-274">Generally, overdraw can be mitigated by culling objects ahead of time before they are sent to the GPU.</span></span> <span data-ttu-id="3e228-275">Unity 提供了有关实施的详细信息[封闭剔除](https://docs.unity3d.com/Manual/OcclusionCulling.html)其引擎。</span><span class="sxs-lookup"><span data-stu-id="3e228-275">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="3e228-276">内存建议</span><span class="sxs-lookup"><span data-stu-id="3e228-276">Memory recommendations</span></span>

<span data-ttu-id="3e228-277">过多的内存分配和解除分配操作可以产生负面影响，从而导致不一致的性能、 冻结的框架和其他造成不利影响的行为在全息版应用程序上。</span><span class="sxs-lookup"><span data-stu-id="3e228-277">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="3e228-278">它是由于内存管理控制垃圾回收器在 Unity 中进行开发时了解内存注意事项尤为重要。</span><span class="sxs-lookup"><span data-stu-id="3e228-278">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="3e228-279">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="3e228-279">Garbage collection</span></span>

<span data-ttu-id="3e228-280">全息版的应用将失去到垃圾回收器 (GC) 处理计算时间时，GC 激活来分析在作用域中不再是在执行过程的对象和它们的内存需要进行发布，因此，可以使其可供重复使用。</span><span class="sxs-lookup"><span data-stu-id="3e228-280">Holographic apps will loose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released so it can be made available for re-use.</span></span> <span data-ttu-id="3e228-281">常量分配和解除分配对象通常需要垃圾回收器更频繁地运行，因此会影响到性能和用户体验。</span><span class="sxs-lookup"><span data-stu-id="3e228-281">Constant allocations and de-allocations will generally require the garbage collector to run more frequently thus hurting performance and user experience.</span></span>

<span data-ttu-id="3e228-282">Unity 提供了一个极好的页面，详细说明了垃圾回收器工作原理和提示，可在内存管理方面编写更高效的代码。</span><span class="sxs-lookup"><span data-stu-id="3e228-282">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="3e228-283">在 Unity 游戏的优化垃圾回收</span><span class="sxs-lookup"><span data-stu-id="3e228-283">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="3e228-284">不会导致过多的垃圾回收的最常见做法之一缓存对组件和 Unity 开发中的类的引用。</span><span class="sxs-lookup"><span data-stu-id="3e228-284">One of the most common practices that leads to excessive garbage collection is not caching references to components and classes in Unity development.</span></span> <span data-ttu-id="3e228-285">应在 start （） 或 Awake() 期间捕获和更高版本的功能，如 update （） 或 LateUpdate() 中重新使用的任何引用。</span><span class="sxs-lookup"><span data-stu-id="3e228-285">Any references should be captured during Start() or Awake() and re-used in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="3e228-286">其他快速提示：</span><span class="sxs-lookup"><span data-stu-id="3e228-286">Other quick tips:</span></span>
- <span data-ttu-id="3e228-287">使用[StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C#类，以动态地生成复杂的字符串，在运行时</span><span class="sxs-lookup"><span data-stu-id="3e228-287">Use the [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="3e228-288">删除对 Debug.Log() 不再需要其仍在所有生成版本的应用程序执行时调用</span><span class="sxs-lookup"><span data-stu-id="3e228-288">Remove calls to Debug.Log() when no longer needed as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="3e228-289">如果您全息版的应用程序通常需要大量内存，请考虑调用[ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)期间加载阶段诸如显示加载时或转换屏幕</span><span class="sxs-lookup"><span data-stu-id="3e228-289">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="3e228-290">对象池</span><span class="sxs-lookup"><span data-stu-id="3e228-290">Object pooling</span></span>

<span data-ttu-id="3e228-291">对象池是一种常用的方法，以降低成本的连续分配和释放的对象。</span><span class="sxs-lookup"><span data-stu-id="3e228-291">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="3e228-292">这是通过分配完全相同的对象的大型池和重新使用从这个池而不是不断地生成和随着时间的推移销毁对象的非活动状态、 可用的实例。</span><span class="sxs-lookup"><span data-stu-id="3e228-292">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="3e228-293">对象池非常适合用于具有变量的生存期期间应用的可重用组件。</span><span class="sxs-lookup"><span data-stu-id="3e228-293">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="3e228-294">对象池在 Unity 中的教程</span><span class="sxs-lookup"><span data-stu-id="3e228-294">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="3e228-295">启动性能</span><span class="sxs-lookup"><span data-stu-id="3e228-295">Startup performance</span></span>

<span data-ttu-id="3e228-296">应考虑使用较小的场景，启动你的应用，然后使用 *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 加载场景的其余部分。</span><span class="sxs-lookup"><span data-stu-id="3e228-296">You should consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="3e228-297">这可让应用能够尽可能快地交互状态。</span><span class="sxs-lookup"><span data-stu-id="3e228-297">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="3e228-298">要注意，可能有较大的 CPU 峰值时激活的新的场景和任何呈现的内容可能会明显变慢或举行的办法。</span><span class="sxs-lookup"><span data-stu-id="3e228-298">Be aware that there may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="3e228-299">若要解决此问题的一种方法是上加载场景 AsyncOperation.allowSceneActivation 属性设置为 false，等待场景中，从而加载，请清除为黑色，屏幕，然后重新设置为 true，则完成场景激活。</span><span class="sxs-lookup"><span data-stu-id="3e228-299">One way to work around this is to set the AsyncOperation.allowSceneActivation property to false on the scene being loaded, wait for the scene to load, clear the screen to black, and then set back to true to complete the scene activation.</span></span>

<span data-ttu-id="3e228-300">请记住，启动场景加载时全息版的初始屏幕将显示给用户。</span><span class="sxs-lookup"><span data-stu-id="3e228-300">Remember that while the startup scene is loading the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e228-301">请参阅</span><span class="sxs-lookup"><span data-stu-id="3e228-301">See also</span></span>
- [<span data-ttu-id="3e228-302">在 Unity 游戏的优化图形呈现</span><span class="sxs-lookup"><span data-stu-id="3e228-302">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="3e228-303">在 Unity 游戏的优化垃圾回收</span><span class="sxs-lookup"><span data-stu-id="3e228-303">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="3e228-304">[物理最佳实践 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="3e228-304">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="3e228-305">[优化脚本 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="3e228-305">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>
