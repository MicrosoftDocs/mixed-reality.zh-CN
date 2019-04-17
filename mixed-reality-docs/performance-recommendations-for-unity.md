---
title: Unity 的性能建议
description: 若要提高性能与混合的现实应用程序的特定于 unity 的提示。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 图形，cpu、 gpu 呈现，垃圾回收 hololens
ms.openlocfilehash: 37eac566a0315009330ac7fee96edd82348d6ba3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593030"
---
# <a name="performance-recommendations-for-unity"></a>Unity 的性能建议

本文基于讨论中所述[混合现实的性能建议](understanding-performance-for-mixed-reality.md)但重点介绍特定于 Unity 引擎环境的知识。

此外，还强烈建议开发人员检查[推荐的环境设置为 Unity 项目](Recommended-settings-for-unity.md)。 本文提供在构建混合现实应用程序的高性能方面的一些最重要的场景配置的内容。 其中的某些建议设置是将突出显示如下。

## <a name="how-to-profile-with-unity"></a>如何使用 Unity 的配置文件

Unity 提供了**[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** 内置这是一个不错的资源，以便收集有价值的性能见解为特定应用。 尽管一个可以运行在编辑器探查器，但这些度量值不表示 true 的运行时环境，因此，应谨慎使用此结果。 建议为远程配置文件正在最准确和可操作见解的设备上运行的应用程序。 进一步来说，Unity[帧调试器](https://docs.unity3d.com/Manual/FrameDebugger.html)也是非常强大和见解工具使用。

Unity 提供了有关的很多文档：
1) 如何连接[Unity 探查器附加到 UWP 应用程序远程](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) 如何有效地[诊断 Unity Profiler 的性能问题](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> 使用连接 Unity Profiler 及添加 GPU 探查器 (请参阅*添加 Profiler*中右上角)，所花费的时间在 CPU 和 GPU 上分别中间探查器，可以看到。 这允许开发人员进行快速估算，如果其应用程序是 CPU 还是 GPU 绑定。
>
> ![Unity CPU vs GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU 性能建议

以下内容介绍了更多的详尽性能做法，尤其是有针对性的 Unity （& a)C#开发。

#### <a name="cache-references"></a>缓存的引用

它是最佳做法是对所有相关的组件和 GameObjects 在初始化时的缓存引用。 这是因为重复函数调用，如*[GetComponent\<T > （)](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 是贵很多相对成本来存储指针的内存。 这也为适用于非常，定期用[Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)。 *Camera.main*实际上就是使用*[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* 越搜索具有的照相机对象在场景图的下方 *"MainCamera"* 标记。

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

>[!NOTE] Avoid GetComponent(string) <br/>
> 使用时 *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*，有少量的不同的重载。 请务必始终使用基于的类型实现，而绝不会基于字符串的搜索重载。 搜索由您的场景中的字符串是明显比搜索由类型成本更高。 <br/>
> （好）组件 GetComponent （类型） <br/>
> （好）T GetComponent\<T > （) <br/>
> （错误）组件 GetComponent(string) > <br/>

#### <a name="avoid-expensive-operations"></a>避免成本高昂的操作

1) **避免使用[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    尽管 LINQ 可以非常干净且轻松地读取和写入，但它通常需要更多的计算和特别详细内存分配比手动写出的算法。

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **常见的 Unity Api**

    某些 Unity Api，虽然有用，可以执行代价很高。 这些大部分涉及搜索整个场景图形的 GameObjects 一些匹配列表。 这些操作通常可以避免缓存引用或实现的相关 Gameobject 来跟踪在运行时引用管理器组件。

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[Sendmessage （)](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 并*[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 应消除不惜一切代价。 这些函数可以是 1000 x 慢于直接函数调用的顺序。

3) **请注意装箱**

    [装箱](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)是一个核心概念的C#语言和运行时。 它是值类型的变量，例如 char、 int、 bool 等包装到引用类型的变量的过程。 值类型变量进行"装箱，"时包装内 System.Object 存储在托管堆上。 因此，分配内存和释放时，最终必须由垃圾回收器处理。 这些分配和释放会产生性能开销和在许多情况下是不必要或可以轻松地替换为成本较低的替代方法。

#### <a name="repeating-code-paths"></a>重复的代码路径

任何重复的 Unity 回调函数 （即 更新） 每秒多次执行和/或应非常仔细地写入帧。 任何成本高昂的操作会对性能产生巨大且一致的影响。

1) **空的回调函数**

    虽然下面的代码可能看起来正常将应用程序，尤其是因为使用此代码块，每个 Unity 脚本自动初始化这些空回调可能实际上会变得非常昂贵。 Unity 通过非托管/托管代码边界，UnityEngine 代码和应用程序代码之间进行往返操作。 即使没有要执行上下文切换此桥非常耗费资源。 这将成为你的应用有 100 个 Gameobject 组件具有空重复 Unity 回调的使用尤其存在问题。

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update （） 是最常见的表现形式这种性能问题，但如下所示其他重复 Unity 回调可以是同样那么糟糕如果不更糟的是：FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc. 

2) **操作更看重运行一次每一帧**

    以下的 Unity Api 都是很多全息版的应用程序的常见操作。 尽管不是始终可行，但这些函数的结果非常通常计算一次，结果重新利用给定的框架在应用程序。

    a） 通常很好的做法具有专用的单一实例类或服务来处理你向场景的视线移动 Raycast，然后在所有其他场景组件，而不是使每个重复和实质上是相同 Raycast 操作重新使用此结果组件。 当然，某些应用程序可能需要从不同的源或针对不同的 raycasts [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)。

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b） 避免 GetComponent() 操作中重复的 Unity 回调，如通过 update （）[缓存引用](#cache-references)start （） 或 Awake() 中

        UnityEngine.Object.GetComponent()

    c） 它是所有对象，如果可能，请在初始化和使用的实例都化的好办法[对象池](#object-pooling)回收并重复整个应用程序的运行时使用 GameObjects

        UnityEngine.Object.Instantiate()

3) **避免接口和虚拟构造**

    调用函数调用通过接口与直接对象或调用虚函数通常情况下可以比使用直接构造或直接函数调用的昂贵得多。 如果虚函数或接口为不必要的则应删除。 但是，性能下降的这些方法通常是值得进行权衡如果利用它们简化了开发协作、 代码的可读性，以及代码可维护性。 

4) **避免通过值传递结构**

    与类不同，结构是值类型，并直接传递到函数，其内容复制到新创建的实例。 此副本将添加的 CPU 开销以及在堆栈上的更多内存。 对于小结构，其效果是通常很少，因此可接受。 但是，对于反复调用函数的每一帧以及函数采用较大的结构，如有可能修改要按引用传递的函数定义。 [此处详细了解](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>其他

1) **物理引擎**

    a） 通常情况下，以提高物理引擎的最简单方法是时间的限制所用的物理或每秒的迭代次数量。 当然，这将减少模拟准确性。 请参阅[TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) Unity 中

    在 Unity 中的碰撞体 b） 该类型具有很大不同的性能特征。 下面的顺序列出了大多数性能碰撞体到最高性能碰撞体从左到右。 它是最重要，以避免网格碰撞体是比基元碰撞体贵很多。

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    请参阅[Unity 物理最佳实践](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)的详细信息

2) **动画**

    通过禁用动画器组件来禁用空闲的动画 （禁用游戏对象不会有相同的效果）。 避免设计模式，其中将动画器放置在一个循环将值设置为相同的操作。 没有增加大量开销，对于此技术，对应用程序没有影响。 [此处了解详情。](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **复杂的算法**

    如果你的应用程序使用反向运动学、 路径查找等复杂的算法，查找要查找更简单的方法或调整其性能的相关设置

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU GPU 性能建议

通常情况下，向下越高，CPU GPU 性能**绘图调用**提交到图形卡。 若要提高性能，绘图调用必须是多个巧妙布局**a） 减少**或**b） 重新构建**以获得最佳效果。 由于自身的绘图调用都是需要消耗大量资源，则减少它们将减少所需的整体工作。 此外，状态的绘图调用之间的更改需要成本高昂的验证和转换中的图形驱动程序的步骤，因此，重新构建的应用程序的绘图调用，以限制状态更改 （即 不同的材料等） 可以提高性能。

Unity 有一种很好的篇文章，概括介绍并深入探讨了批处理其平台的绘图调用。
- [Unity 绘制调用批处理](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>单个传递实例的呈现

在 Unity 中的单次传递 Instanced 呈现允许每只眼睛降低下一个实例化的绘图调用的绘图调用。 由于两个绘图调用之间的缓存一致性，还提供了一些性能改进以及在 GPU 上。

若要启用此功能在 Unity 项目中
1)  打开**播放器 XR 设置**(转到**编辑** > **项目设置** > **播放机** > **XR 设置**)
2) 选择**单个传递二次实例化**从**立体声呈现方法**下拉列表菜单 (**虚拟现实支持**必须选中复选框)

阅读以下文章 Unity 中使用此方法时呈现的详细信息。
- [如何使用高级立体声呈现 AR 和 VR 性能最大化](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [单次传递实例化](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 如果开发人员已具有没有为编写的现有自定义着色器，会发生与单个传递实例呈现一个常见的问题实例化。 启用此功能后, 开发人员可能会注意到某些 GameObjects 仅呈现一眼中。 这是因为关联的自定义着色器不具有适当的属性为实例化。
>
> 请参阅[单个传递立体声的呈现 HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)从 Unity 如何解决此问题

#### <a name="static-batching"></a>静态批处理

Unity 是能够批处理多个静态对象，以减少到 GPU 的绘图调用。 静态批处理适用于大多数[呈现器](https://docs.unity3d.com/ScriptReference/Renderer.html)Unity 中的对象的**1） 共享同一种材料**并**2） 是所有标记为*静态*** (在 Unity 中选择一个对象，然后单击右上角的复选框右侧的检查器)。 标记为 GameObjects*静态*整个应用程序的运行时不能移动。 因此，静态批处理可能很难利用的 HoloLens 需要放置，已移动、 缩放等几乎每个对象上。对于沉浸式耳机，静态批处理可以显著减少的绘图调用并因此提高性能。

读取*静态批处理*下[绘制调用批处理在 Unity 中](https://docs.unity3d.com/Manual/DrawCallBatching.html)的更多详细信息。

#### <a name="dynamic-batching"></a>动态批处理

由于它是有问题，若要将对象标记为*静态*对于 HoloLens 开发动态批处理可以是一个强大的工具对此进行弥补缺少功能。 当然，这是可以也十分有用也沉浸式耳机。 在 Unity 中的动态批处理很难但若要启用，因为必须 GameObjects **a） 共享同一种材料**和**b） 满足其他条件一长串**。

读取*动态批处理*下[绘制调用批处理在 Unity 中](https://docs.unity3d.com/Manual/DrawCallBatching.html)的完整列表。 大多数情况下，GameObjects 变为无效，因为关联的网格数据可以是不能超过 300 顶点动态批处理。

#### <a name="other-techniques"></a>其他技术

如果多个 GameObjects 可以共享同一种材料，可以仅发生批处理。 通常这将阻止 GameObjects 若要为其各自的材料具有唯一的纹理的需求。 通常会将纹理组合成一个大的纹理，一种称为方法[纹理 Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)。

此外，通常最好是将合并到一个 GameObject 的网格，可能和合理的位置。 在 Unity 中的每个呈现器会将其与提交下一个呈现器组合的网格的绘图调用相关联。 

>[!NOTE]
> 修改在运行时的 Renderer.material 属性将创建的材料的副本，并因此可能会中断批处理。 使用 Renderer.sharedMaterial 跨 GameObjects 修改共享的 material 属性。

## <a name="gpu-performance-recommendations"></a>GPU 性能建议

详细了解[优化在 Unity 中的图形呈现](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

#### <a name="reduce-poly-count"></a>减少 poly 计数

多边形计数通常会减少通过以下任一方法
1) 从一个场景中删除对象
2) 它可以减少为给定的网格的多边形资产抽取
3) 实现[的详细信息级别 (LOD) 系统](https://docs.unity3d.com/Manual/LevelOfDetail.html)到应用程序来呈现远而具有较低多边形版本的同一个几何对象

#### <a name="limit-overdraw"></a>限制过度绘制

在 Unity 中，其中一个可以显示过度绘制为其场景中，通过切换[**绘图模式菜单**](https://docs.unity3d.com/Manual/ViewModes.html)中的左上角**场景视图**并选择**过度绘制**.

通常情况下，过度绘制可缓解通过剔除提前发送到 GPU 前的对象。 Unity 提供了有关实施的详细信息[封闭剔除](https://docs.unity3d.com/Manual/OcclusionCulling.html)其引擎。

#### <a name="understanding-shaders-in-unity"></a>了解在 Unity 中的着色器

轻松近似值进行比较的性能的着色器是确定每个操作的平均数目将在运行时执行。 这可以在 Unity 中相当轻松地实现。

1) 选择你的着色器资产或其他营销材料，然后在检查器窗口的右上角，选择齿轮图标，然后 **"选择着色器"**

    ![选择在 Unity 中的着色器](images/Select-shader-unity.png)
2) 与所选着色器资产，请单击 **"编译和显示代码"** 按钮下的检查器窗口

    ![编译中 Unity 着色器代码](images/compile-shader-code-unity.PNG)

3) 编译后，查看统计信息部分结果中的顶点和像素着色器为不同的操作数目 (注意： 像素着色器通常也称为片段着色器)

    ![Unity 标准着色器操作](images/unity-standard-shader-compilation.png)

##### <a name="unity-standard-shader-alternatives"></a>Unity 标准着色器替代项

而不是使用以物理方式根据的呈现 (PBR) 或其他高质量着色器，看看利用更高的性能和成本更低的着色器。 [混合现实 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供了[标准着色器](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader)已针对混合的现实项目进行优化的。

Unity 也提供了向标准 Unity 着色器的不亮、 亮起顶点、 明显更快地进行比较的漫射，和其他简化着色器选项。 请参阅[使用情况和内置着色器性能](https://docs.unity3d.com/Manual/shader-Performance.html)更多详细信息。

## <a name="memory-recommendations"></a>内存建议

过多的内存分配和解除分配操作可以产生负面影响，从而导致不一致的性能、 冻结的框架和其他造成不利影响的行为在全息版应用程序上。 它是由于内存管理控制垃圾回收器在 Unity 中进行开发时了解内存注意事项尤为重要。

#### <a name="garbage-collection"></a>垃圾回收

全息版的应用将失去到垃圾回收器 (GC) 处理计算时间时，GC 激活来分析在作用域中不再是在执行过程的对象和它们的内存需要进行发布，因此，可以使其可供重复使用。 常量分配和解除分配对象通常需要垃圾回收器更频繁地运行，因此会影响到性能和用户体验。

Unity 提供了一个极好的页面，详细说明了垃圾回收器工作原理和提示，可在内存管理方面编写更高效的代码。
- [在 Unity 游戏的优化垃圾回收](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

不会导致过多的垃圾回收的最常见做法之一缓存对组件和 Unity 开发中的类的引用。 应在 start （） 或 Awake() 期间捕获和更高版本的功能，如 update （） 或 LateUpdate() 中重新使用的任何引用。

其他快速提示：
- 使用[StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C#类，以动态地生成复杂的字符串，在运行时
- 删除对 Debug.Log() 不再需要其仍在所有生成版本的应用程序执行时调用
- 如果您全息版的应用程序通常需要大量内存，请考虑调用[ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)期间加载阶段诸如显示加载时或转换屏幕

#### <a name="object-pooling"></a>对象池

对象池是一种常用的方法，以降低成本的连续分配和释放的对象。 这是通过分配完全相同的对象的大型池和重新使用从这个池而不是不断地生成和随着时间的推移销毁对象的非活动状态、 可用的实例。 对象池非常适合用于具有变量的生存期期间应用的可重用组件。

- [对象池在 Unity 中的教程](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>启动性能

应考虑使用较小的场景，启动你的应用，然后使用*[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 加载场景的其余部分。 这可让应用能够尽可能快地交互状态。 要注意，可能有较大的 CPU 峰值时激活的新的场景和任何呈现的内容可能会明显变慢或举行的办法。 若要解决此问题的一种方法是上加载场景 AsyncOperation.allowSceneActivation 属性设置为 false，等待场景中，从而加载，请清除为黑色，屏幕，然后重新设置为 true，则完成场景激活。

请记住，启动场景加载时全息版的初始屏幕将显示给用户。

## <a name="see-also"></a>请参阅
- [在 Unity 游戏的优化图形呈现](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [在 Unity 游戏的优化垃圾回收](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [物理最佳实践 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [优化脚本 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
