---
title: Unity 中的空间映射
description: 在 Unity 中呈现并与真实世界几何发生冲突。
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 空间映射, 呈现器, 碰撞器, 网格, 扫描, 组件
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148650"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="ac2ed-104">Unity 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="ac2ed-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="ac2ed-105">本主题介绍如何在 Unity 项目中使用[空间映射](spatial-mapping.md), 以及如何在 HoloLens 设备上检索表示世界上的表面的三角形网格, 以便进行放置、封闭、房间分析等。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="ac2ed-106">Unity 包含对空间映射的完全支持, 可通过以下方式向开发人员公开:</span><span class="sxs-lookup"><span data-stu-id="ac2ed-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="ac2ed-107">MixedRealityToolkit 中提供了空间映射组件, 可为空间映射入门提供方便快捷的路径</span><span class="sxs-lookup"><span data-stu-id="ac2ed-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="ac2ed-108">较低级别的空间映射 Api, 提供完全控制并实现更复杂的特定于应用程序的自定义</span><span class="sxs-lookup"><span data-stu-id="ac2ed-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="ac2ed-109">若要在应用中使用空间映射, 需要在 Appxmanifest.xml 中设置 spatialPerception 功能。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="ac2ed-110">设置 SpatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="ac2ed-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="ac2ed-111">为了使应用程序能够使用空间映射数据, 必须启用 SpatialPerception 功能。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="ac2ed-112">如何启用 SpatialPerception 功能:</span><span class="sxs-lookup"><span data-stu-id="ac2ed-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="ac2ed-113">在 Unity 编辑器中, 打开 **"播放机设置"** 窗格 (编辑 > Player > 项目设置)</span><span class="sxs-lookup"><span data-stu-id="ac2ed-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="ac2ed-114">单击 **"Windows 应用商店"** 选项卡</span><span class="sxs-lookup"><span data-stu-id="ac2ed-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="ac2ed-115">展开 **"发布设置"** , 然后在 **"功能"** 列表中检查 **"SpatialPerception"** 功能</span><span class="sxs-lookup"><span data-stu-id="ac2ed-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="ac2ed-116">请注意, 如果已将 Unity 项目导出到 Visual Studio 解决方案, 则需要导出到新文件夹或[在 Visual studio 的 appxmanifest.xml 中手动设置此功能](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="ac2ed-117">空间映射还需要至少10.0.10586.0 的 MaxVersionTested:</span><span class="sxs-lookup"><span data-stu-id="ac2ed-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="ac2ed-118">在 Visual Studio 中, 右键单击 "解决方案资源管理器中的**appxmanifest.xml** , 然后选择"**查看代码**"</span><span class="sxs-lookup"><span data-stu-id="ac2ed-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="ac2ed-119">查找指定**y**的行, 并将**MaxVersionTested = "10.0.10240.0"** 更改为**MaxVersionTested = "10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="ac2ed-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="ac2ed-120">**保存**appxmanifest.xml。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="ac2ed-121">Unity 内置空间映射组件入门</span><span class="sxs-lookup"><span data-stu-id="ac2ed-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="ac2ed-122">Unity 提供了2个组件, 可轻松地将空间映射添加到应用、**空间映射呈现**器和**空间映射碰撞**器。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="ac2ed-123">空间映射呈现器</span><span class="sxs-lookup"><span data-stu-id="ac2ed-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="ac2ed-124">空间映射呈现器允许对空间映射网格进行可视化。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Unity 中的空间映射呈现器](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="ac2ed-126">空间映射碰撞器</span><span class="sxs-lookup"><span data-stu-id="ac2ed-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="ac2ed-127">空间映射碰撞器允许通过空间映射网格进行全息内容 (或字符) 交互, 如物理学。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Unity 中的空间映射碰撞器](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="ac2ed-129">使用内置的空间映射组件</span><span class="sxs-lookup"><span data-stu-id="ac2ed-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="ac2ed-130">如果要可视化和与物理表面交互, 则可以将这两个组件添加到应用中。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="ac2ed-131">在 Unity 应用中使用这两个组件:</span><span class="sxs-lookup"><span data-stu-id="ac2ed-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="ac2ed-132">在要检测空间图面网格的区域的中心选择一个 GameObject。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="ac2ed-133">在检查器窗口中,**添加组件** > **XR** > **空间映射碰撞** 器或**空间映射呈现**器。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="ac2ed-134">有关如何在<a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 文档网站</a>上使用这些组件的详细信息, 请参阅。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="ac2ed-135">超越内置的空间映射组件</span><span class="sxs-lookup"><span data-stu-id="ac2ed-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="ac2ed-136">利用这些组件, 您可以轻松地开始进行空间映射。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="ac2ed-137"> 若要进一步了解, 需要了解两个主要的路径:</span><span class="sxs-lookup"><span data-stu-id="ac2ed-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="ac2ed-138">若要执行自己的低级网格处理, 请参阅下面有关低级别空间映射脚本 API 的部分。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="ac2ed-139">若要执行更高级别的网格分析, 请参阅以下部分, 了解<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>中的 SpatialUnderstanding 库。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="ac2ed-140">使用低级别 Unity 空间映射 API</span><span class="sxs-lookup"><span data-stu-id="ac2ed-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="ac2ed-141">如果需要更多的控制, 而不是从空间映射呈现器和空间映射碰撞器组件获取, 则可以使用低级空间映射脚本 Api。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="ac2ed-142">**命名空间：**  *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="ac2ed-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="ac2ed-143">**类型**: *SurfaceObserver*、 *SurfaceChange*、 *SurfaceData*、 *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="ac2ed-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="ac2ed-144">下面是使用空间映射 Api 的应用程序的建议流概述。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="ac2ed-145">设置 SurfaceObserver</span><span class="sxs-lookup"><span data-stu-id="ac2ed-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="ac2ed-146">为需要空间映射数据的每个应用程序定义的空间区域实例化一个 SurfaceObserver 对象。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="ac2ed-147">通过调用 SetVolumeAsSphere、SetVolumeAsAxisAlignedBox、SetVolumeAsOrientedBox 或 SetVolumeAsFrustum, 指定每个 SurfaceObserver 对象将为其提供数据的空间区域。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="ac2ed-148">您可以重新定义将来的空间区域, 只需再次调用其中一种方法即可。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="ac2ed-149">调用 SurfaceObserver () 时, 必须为空间映射系统包含其新信息的空间的 SurfaceObserver 区域中的每个空间图面提供一个处理程序。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="ac2ed-150">对于一个空间图面, 处理程序接收:</span><span class="sxs-lookup"><span data-stu-id="ac2ed-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="ac2ed-151">处理表面更改</span><span class="sxs-lookup"><span data-stu-id="ac2ed-151">Handling Surface Changes</span></span>

<span data-ttu-id="ac2ed-152">有几个用来处理的主要用例。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-152">There are several main cases to handle.</span></span> <span data-ttu-id="ac2ed-153">添加了 & 更新, 可以使用相同的代码路径并将其删除。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="ac2ed-154">在示例中添加的 & 更新的事例中, 我们从字典中添加或获取表示此网格的 GameObject, 使用必要的组件创建 SurfaceData 结构, 然后调用 RequestMeshDataAsync 用网格数据填充 GameObject, 并场景中的位置。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="ac2ed-155">在已删除的示例中, 我们从字典中删除表示此网格的 GameObject 并销毁它。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a><span data-ttu-id="ac2ed-156">处理数据准备就绪</span><span class="sxs-lookup"><span data-stu-id="ac2ed-156">Handling Data Ready</span></span>

<span data-ttu-id="ac2ed-157">OnDataReady 处理程序接收 SurfaceData 对象。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="ac2ed-158">它包含的 WorldAnchor、MeshFilter 和 (可选) MeshCollider 对象反映了关联空间图面的最新状态。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="ac2ed-159">还可以通过访问 MeshFilter 对象的网格成员来执行分析和/或[处理](spatial-mapping.md#mesh-processing)网格数据。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="ac2ed-160">使用最新网格呈现空间图面, 并 (可选) 使用它来实现物理学冲突和 raycasts。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="ac2ed-161">务必确认 SurfaceData 的内容不为空。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="ac2ed-162">开始处理更新</span><span class="sxs-lookup"><span data-stu-id="ac2ed-162">Start processing on updates</span></span>

<span data-ttu-id="ac2ed-163">应延迟 (而不是每个帧) 调用 SurfaceObserver ()。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="ac2ed-164">更高级别的网格分析:SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="ac2ed-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="ac2ed-165"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>是一系列有用的实用工具代码, 适用于基于全息 Unity api 构建的全息开发。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="ac2ed-166">空间理解</span><span class="sxs-lookup"><span data-stu-id="ac2ed-166">Spatial Understanding</span></span>

<span data-ttu-id="ac2ed-167">在物理环境中放置全息影像时, 通常需要超越空间映射的网格和面平面。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="ac2ed-168">过程放置完成后, 需要更高级别的环境理解。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="ac2ed-169">这通常需要作出有关楼层、天花板和墙壁的决策。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="ac2ed-170">此外, 还可以根据一组放置约束进行优化, 以确定全息对象的最理想物理位置。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="ac2ed-171">在 Conker 和片段的开发过程中, Asobo 工作室面临着这一问题, 开发一个房间规划求解来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="ac2ed-172">其中每个游戏都具有游戏特定需求, 但它们共享了核心空间理解技术。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="ac2ed-173">HoloToolkit SpatialUnderstanding 库封装了这一技术, 使你能够快速找到墙上的空白空间, 将对象放置在天花板上, 识别出要放置的字符, 以及其他大量的空间理解查询。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="ac2ed-174">所有源代码都包含在内, 使你可以根据需要对其进行自定义, 并与社区分享你的改进。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="ac2ed-175">C++规划求解的代码已包装到 UWP dll 中, 并通过包含在 MixedRealityToolkit 内的 prefab 中向 Unity 公开。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="ac2ed-176">了解模块</span><span class="sxs-lookup"><span data-stu-id="ac2ed-176">Understanding Modules</span></span>

<span data-ttu-id="ac2ed-177">模块公开了三个主要接口: 用于简单图面和空间查询的拓扑、用于对象检测的形状, 以及用于基于约束的对象集放置的对象放置规划求解。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="ac2ed-178">下面介绍了其中的每个。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-178">Each of these is described below.</span></span> <span data-ttu-id="ac2ed-179">除了三个主要模块接口外, ray 强制转换接口还可用于检索标记的表面类型, 并可将自定义 watertight playspace 网格复制出来。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="ac2ed-180">Ray 转换</span><span class="sxs-lookup"><span data-stu-id="ac2ed-180">Ray Casting</span></span>

<span data-ttu-id="ac2ed-181">在房间经过扫描并完成后, 会在内部生成标签, 如地面、天花板和墙。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="ac2ed-182">"PlayspaceRaycast" 函数采用 ray, 如果该射线与已知表面冲突, 则返回, 如果是, 则返回 "RaycastResult" 形式的有关该曲面的信息。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="ac2ed-183">在内部, raycast 是针对 playspace 的计算8cm 立方 voxel 表示法计算的。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="ac2ed-184">每个 voxel 包含一组具有已处理拓扑数据 (也称为 surfels) 的 surface 元素。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="ac2ed-185">将比较交叉 voxel 单元中包含的 surfels 和用于查找拓扑信息的最佳匹配项。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="ac2ed-186">此拓扑数据包含以 "SurfaceTypes" 枚举形式返回的标签, 以及相交表面的外围应用。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="ac2ed-187">在 Unity 示例中, 游标将每个帧都转换为射线。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="ac2ed-188">首先, 针对 Unity 的 colliders。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="ac2ed-189">其次, 针对 "了解模块" 的世界表示。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="ac2ed-190">最后又是一个 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-190">And finally, again UI elements.</span></span> <span data-ttu-id="ac2ed-191">在此应用程序中, UI 获得优先级, 接下来是理解结果, 最后是 Unity colliders。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="ac2ed-192">SurfaceType 将报告为光标旁边的文本。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="ac2ed-193">![曲面类型在光标旁边标记](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ac2ed-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="ac2ed-194">*曲面类型在光标旁边标记*</span><span class="sxs-lookup"><span data-stu-id="ac2ed-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="ac2ed-195">拓扑查询</span><span class="sxs-lookup"><span data-stu-id="ac2ed-195">Topology Queries</span></span>

<span data-ttu-id="ac2ed-196">在 DLL 中, 拓扑管理器处理环境的标记。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="ac2ed-197">如上所述, 很多数据存储在 surfels 中, 包含在 voxel 卷中。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="ac2ed-198">此外, "PlaySpaceInfos" 结构用于存储有关 playspace 的信息, 其中包括世界对齐 (有关此内容的更多详细信息)、楼层和天花板高度。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="ac2ed-199">试探法用于确定地面、天花板和墙。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="ac2ed-200">例如, 具有大于1个 m2 面区的最大和最低水平曲面被视为楼层。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="ac2ed-201">请注意, 在此过程中也使用了扫描过程中的照相机路径。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="ac2ed-202">拓扑管理器公开的查询子集通过 dll 公开。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="ac2ed-203">公开的拓扑查询如下所示。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="ac2ed-204">每个查询都具有一组特定于查询类型的参数。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="ac2ed-205">在下面的示例中, 用户指定了所需的卷的最小高度 & 宽度、地面上的最小位置高度以及卷前面的最小间隙量。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="ac2ed-206">所有度量都以米为单位。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="ac2ed-207">其中每个查询都使用 "TopologyResult" 结构的预分配数组。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="ac2ed-208">"LocationCount" 参数指定传入数组的长度。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="ac2ed-209">返回值报告返回的位置的数量。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="ac2ed-210">此数字绝不会大于 "locationCount" 参数中传递的值。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="ac2ed-211">"TopologyResult" 包含返回的卷的中心位置、定向方向 (即普通) 以及找到的空间的尺寸。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="ac2ed-212">请注意, 在 Unity 示例中, 其中每个查询都链接到 "虚拟 UI" 面板中的某个按钮。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="ac2ed-213">示例将每个查询的参数硬编码为合理的值。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="ac2ed-214">有关更多示例, 请参阅示例代码中的 SpaceVisualizer.cs。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="ac2ed-215">形状查询</span><span class="sxs-lookup"><span data-stu-id="ac2ed-215">Shape Queries</span></span>

<span data-ttu-id="ac2ed-216">在 dll 的内部, 形状分析器 ("ShapeAnalyzer_W") 使用拓扑分析器与用户定义的自定义形状相匹配。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="ac2ed-217">Unity 示例定义一组形状, 并通过 "应用内查询" 菜单在 "形状" 选项卡中公开结果。其目的在于, 用户可以根据应用程序的需要定义自己的对象形状查询并使用这些查询。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="ac2ed-218">请注意, 形状分析仅适用于水平曲面。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="ac2ed-219">例如, 沙发由平面座位表面和沙发顶部的扁平顶部定义。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="ac2ed-220">形状查询查找特定大小、高度和方位范围的两个图面, 两个图面对齐并连接起来。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="ac2ed-221">使用 Api 术语, 沙发座位和后端是形状组件, 对齐要求是形状组件约束。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="ac2ed-222">下面是 Unity 示例 (ShapeDefinition.cs) 中为 "sittable" 对象定义的示例查询。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="ac2ed-223">每个形状查询都由一组形状组件定义, 每个形状组件都具有一组组件约束和一组形状约束, 它们列出组件之间的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="ac2ed-224">此示例在单个组件定义中包含三个约束, 组件之间没有任何形状约束 (因为只有一个组件)。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="ac2ed-225">与此相反, 沙发形状具有两个形状组件和四个形状约束。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="ac2ed-226">请注意, 组件由其在用户的组件列表中的索引标识 (在本示例中为0和 1)。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="ac2ed-227">在 Unity 模块中提供包装函数以便于创建自定义形状定义。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="ac2ed-228">可以在 "ShapeComponentConstraint" 和 "ShapeConstraint" 结构内的 "SpatialUnderstandingDll.cs" 中找到组件和形状约束的完整列表。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="ac2ed-229">![在此图面上找到矩形形状](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ac2ed-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="ac2ed-230">*在此图面上找到矩形形状*</span><span class="sxs-lookup"><span data-stu-id="ac2ed-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="ac2ed-231">对象放置规划求解</span><span class="sxs-lookup"><span data-stu-id="ac2ed-231">Object Placement Solver</span></span>

<span data-ttu-id="ac2ed-232">对象放置规划求解可用于确定放置对象的物理空间中的理想位置。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="ac2ed-233">在给定对象规则和约束的情况下, 求解器将找到最适合的位置。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="ac2ed-234">此外, 对象查询会一直保留, 直到删除了具有 "Solver_RemoveObject" 或 "Solver_RemoveAllObjects" 调用的对象, 从而允许约束的多对象位置。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="ac2ed-235">对象放置查询由三个部分组成: 具有参数的放置类型、规则列表和约束列表。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="ac2ed-236">若要运行查询, 请使用以下 API。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-236">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="ac2ed-237">此函数采用对象名称、位置定义和规则和约束列表。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="ac2ed-238">C#包装器提供构造帮助器函数, 可简化规则和约束构造。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="ac2ed-239">放置定义包含查询类型, 即以下其中一项。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-239">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

<span data-ttu-id="ac2ed-240">每个放置类型都具有一组特定于该类型的参数。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="ac2ed-241">"ObjectPlacementDefinition" 结构包含一组静态 helper 函数, 用于创建这些定义。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="ac2ed-242">例如, 若要查找在楼层上放置对象的位置, 可以使用以下函数。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="ac2ed-243">public static ObjectPlacementDefinition Create_OnFloor (System.numerics.vector2 halfDims) 除了放置类型之外, 还可以提供一组规则和约束。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="ac2ed-244">不能违反规则。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-244">Rules cannot be violated.</span></span> <span data-ttu-id="ac2ed-245">然后, 将根据一组约束优化满足类型和规则的可能放置位置, 以便选择最佳放置位置。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="ac2ed-246">每个规则和约束都可以通过提供的静态创建函数来创建。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="ac2ed-247">下面提供了一个示例规则和约束构造函数。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="ac2ed-248">以下对象放置查询正在寻找一个位置, 用于将半米式立方体放置在表面的边缘, 远离其他以前放置的对象, 靠近房间的中心。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="ac2ed-249">如果成功, 则返回包含放置位置、尺寸和方向的 "ObjectPlacementResult" 结构。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="ac2ed-250">此外, 放置将添加到 dll 的已放置对象的内部列表中。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="ac2ed-251">后续的放置查询会将此对象考虑在内。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="ac2ed-252">Unity 示例中的 "LevelSolver.cs" 文件包含更多示例查询。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="ac2ed-253">![对象放置的结果](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ac2ed-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="ac2ed-254">*图 3:蓝框, 如何将三个位置上的结果从照相机位置规则移开*</span><span class="sxs-lookup"><span data-stu-id="ac2ed-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="ac2ed-255">当对级别或应用程序方案所需的多个对象的放置位置进行求解时, 首先要解决不必要的对象和大型对象, 以便最大程度地提高空间。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="ac2ed-256">放置顺序很重要。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-256">Placement order is important.</span></span> <span data-ttu-id="ac2ed-257">如果找不到对象位置, 请尝试减少不受约束的配置。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="ac2ed-258">具有一组后备配置对于跨许多房间配置支持功能至关重要。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="ac2ed-259">房间扫描过程</span><span class="sxs-lookup"><span data-stu-id="ac2ed-259">Room Scanning Process</span></span>

<span data-ttu-id="ac2ed-260">虽然 HoloLens 提供的空间映射解决方案设计为能够满足整个范围的问题空间的通用需求, 但却构建了空间理解模块来支持两个特定游戏的需求。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="ac2ed-261">其解决方案是围绕特定过程和假设集构造的, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="ac2ed-262">用户驱动的 playspace "painting" –在扫描阶段, 用户会四处移动并四处四处旋转, 从而有效地绘制应包括的区域。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="ac2ed-263">在此阶段, 生成的网格非常重要, 可提供用户反馈。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="ac2ed-264">室内家庭或办公设置–查询函数围绕平整表面和墙壁围绕直角设计。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="ac2ed-265">这是一个软限制。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-265">This is a soft limitation.</span></span> <span data-ttu-id="ac2ed-266">但是, 在扫描阶段, 将完成主轴分析以按主要轴和次要轴优化网格分割。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="ac2ed-267">包含的 SpatialUnderstanding.cs 文件管理扫描阶段过程。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="ac2ed-268">它调用以下函数。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-268">It calls the following functions.</span></span>

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

<span data-ttu-id="ac2ed-269">由 "SpatialUnderstanding" 行为驱动的扫描流将调用 InitScan, 然后 UpdateScan 每个帧。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="ac2ed-270">当统计信息查询报告合理的范围时, 允许用户 airtap 调用 RequestFinish 以指示扫描阶段结束。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="ac2ed-271">继续调用 UpdateScan, 直到返回值指示 dll 已完成处理。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="ac2ed-272">了解网格</span><span class="sxs-lookup"><span data-stu-id="ac2ed-272">Understanding Mesh</span></span>

<span data-ttu-id="ac2ed-273">理解 dll 在内部将 playspace 存储为8cm 大小 voxel 多维数据集的网格。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="ac2ed-274">在扫描的初始部分中, 将完成主要组件分析以确定房间的轴。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="ac2ed-275">在内部, 它存储其 voxel 空间与这些轴对齐。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="ac2ed-276">大约每秒生成一次网格, 方法是从 voxel 卷中提取等值面。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="ac2ed-277">![从 voxel 卷生成的生成的网格](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="ac2ed-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="ac2ed-278">*从 voxel 卷生成的生成的网格*</span><span class="sxs-lookup"><span data-stu-id="ac2ed-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="ac2ed-279">疑难解答</span><span class="sxs-lookup"><span data-stu-id="ac2ed-279">Troubleshooting</span></span>
* <span data-ttu-id="ac2ed-280">确保已设置[SpatialPerception](#setting-the-spatialperception-capability)功能</span><span class="sxs-lookup"><span data-stu-id="ac2ed-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="ac2ed-281">跟踪丢失时, 下一个 OnSurfaceChanged 事件将删除所有网格。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="ac2ed-282">混合现实工具包中的空间映射</span><span class="sxs-lookup"><span data-stu-id="ac2ed-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="ac2ed-283">有关将空间映射用于混合现实工具包 v2 的详细信息, 请参阅 MRTK 文档的<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">空间感知部分</a>。</span><span class="sxs-lookup"><span data-stu-id="ac2ed-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac2ed-284">请参阅</span><span class="sxs-lookup"><span data-stu-id="ac2ed-284">See also</span></span>
* [<span data-ttu-id="ac2ed-285">MR 空间 230：空间映射</span><span class="sxs-lookup"><span data-stu-id="ac2ed-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="ac2ed-286">坐标系统</span><span class="sxs-lookup"><span data-stu-id="ac2ed-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="ac2ed-287">Unity 中的坐标系统</span><span class="sxs-lookup"><span data-stu-id="ac2ed-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="ac2ed-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="ac2ed-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="ac2ed-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="ac2ed-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="ac2ed-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="ac2ed-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="ac2ed-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine</a></span><span class="sxs-lookup"><span data-stu-id="ac2ed-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
