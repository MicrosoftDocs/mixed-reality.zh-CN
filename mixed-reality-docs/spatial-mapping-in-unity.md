---
title: 在 Unity 中的空间映射
description: 呈现和与其碰撞周围 Unity 中的实际的几何图形。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、 空间映射，呈现器、 碰撞体、 网格、 扫描、 组件
ms.openlocfilehash: f938f5921cb2c06342a9ebcd376d690c10584df9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593079"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="e4bb6-104">在 Unity 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="e4bb6-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="e4bb6-105">本主题介绍如何使用[空间映射](spatial-mapping.md)在 Unity 项目中，检索表示用于放置、 封闭、 空间分析和的详细信息的 HoloLens 设备周围的世界中表面的三角形网格。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="e4bb6-106">Unity 包括对空间映射，按以下方式公开给开发人员的完全支持：</span><span class="sxs-lookup"><span data-stu-id="e4bb6-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="e4bb6-107">空间映射 MixedRealityToolkit 中可用的组件，其中提供的方便和快速路径入门空间映射</span><span class="sxs-lookup"><span data-stu-id="e4bb6-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="e4bb6-108">空间映射较低级别 Api，为提供的完全控制并启用更复杂的应用程序特定自定义</span><span class="sxs-lookup"><span data-stu-id="e4bb6-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="e4bb6-109">若要在应用中使用空间的映射，spatialPerception 功能需要在你的 AppxManifest 中设置。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="e4bb6-110">设置 SpatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="e4bb6-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="e4bb6-111">若要使用空间的映射数据的应用，必须启用 SpatialPerception 功能。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="e4bb6-112">如何启用 SpatialPerception 功能：</span><span class="sxs-lookup"><span data-stu-id="e4bb6-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="e4bb6-113">在 Unity 编辑器中打开 **"播放器设置"** 窗格 (编辑 > 项目设置 > 播放机)</span><span class="sxs-lookup"><span data-stu-id="e4bb6-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="e4bb6-114">单击 **"Windows 应用商店"** 选项卡</span><span class="sxs-lookup"><span data-stu-id="e4bb6-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="e4bb6-115">展开 **"发布设置"** ，并检查 **"SpatialPerception"** 中的功能 **"功能"** 列表</span><span class="sxs-lookup"><span data-stu-id="e4bb6-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="e4bb6-116">请注意，是否你已向 Visual Studio 解决方案导出你的 Unity 项目，你将需要导出到新文件夹或手动[在 Visual Studio 中的 AppxManifest 中设置此功能](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="e4bb6-117">空间映射还需要至少 10.0.10586.0 MaxVersionTested:</span><span class="sxs-lookup"><span data-stu-id="e4bb6-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="e4bb6-118">在 Visual Studio 中，右键单击**Package.appxmanifest**在解决方案资源管理器中，选择**查看代码**</span><span class="sxs-lookup"><span data-stu-id="e4bb6-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="e4bb6-119">查找行指定**TargetDeviceFamily**并将更改**MaxVersionTested ="10.0.10240.0"** 到**MaxVersionTested ="10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="e4bb6-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="e4bb6-120">**保存**Package.appxmanifest。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="e4bb6-121">开始使用 Unity 的内置空间映射组件</span><span class="sxs-lookup"><span data-stu-id="e4bb6-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="e4bb6-122">Unity 提供两个组件： 用于轻松地添加到应用中，空间映射**空间映射呈现器**并**空间映射碰撞体**。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="e4bb6-123">空间映射呈现器</span><span class="sxs-lookup"><span data-stu-id="e4bb6-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="e4bb6-124">空间映射呈现器允许的空间的映射网格的可视化效果。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![空间映射在 Unity 中的呈现器](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="e4bb6-126">空间映射碰撞体</span><span class="sxs-lookup"><span data-stu-id="e4bb6-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="e4bb6-127">空间映射碰撞体允许 holographic 内容 （或字符） 交互，如物理引擎，与空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![在 Unity 中的空间映射碰撞体](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="e4bb6-129">使用内置空间映射组件</span><span class="sxs-lookup"><span data-stu-id="e4bb6-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="e4bb6-130">如果你想要同时可视化和与物理面进行交互，您可以向您的应用程序中添加这两个组件。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="e4bb6-131">若要在 Unity 应用中使用这两个组件：</span><span class="sxs-lookup"><span data-stu-id="e4bb6-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="e4bb6-132">选择要在其中检测空间图面上的网格区域的中心在一个 GameObject。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="e4bb6-133">在检查器窗口中，**添加组件** > **XR** > **空间映射碰撞体** 或**空间映射呈现器**。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="e4bb6-134">有关如何使用这些组件在更多详细信息<a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 文档站点</a>。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="e4bb6-135">超越内置空间映射组件</span><span class="sxs-lookup"><span data-stu-id="e4bb6-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="e4bb6-136">这些组件使其拖放轻松开始使用空间的映射。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="e4bb6-137"> 当你想要更进一步时，有两个主要路径浏览：</span><span class="sxs-lookup"><span data-stu-id="e4bb6-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="e4bb6-138">为你自己的较低级别网格处理，请参阅下面有关的低级别的空间映射脚本 API 的一节。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="e4bb6-139">若要进行更高级别的网格分析时，请参阅下面有关 SpatialUnderstanding 库中的一节<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="e4bb6-140">使用低级别 Unity 空间映射 API</span><span class="sxs-lookup"><span data-stu-id="e4bb6-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="e4bb6-141">如果需要更多的控制不是获得的空间映射的呈现器和空间映射碰撞体组件，可以使用低级别的空间映射脚本 Api。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="e4bb6-142">\**命名空间：\*\*\*UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="e4bb6-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="e4bb6-143">**类型**:*SurfaceObserver*， *SurfaceChange*， *SurfaceData*， *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="e4bb6-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="e4bb6-144">以下是使用空间的映射 Api 的应用程序的建议流程的概述。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="e4bb6-145">设置 SurfaceObserver(s)</span><span class="sxs-lookup"><span data-stu-id="e4bb6-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="e4bb6-146">实例化一个 SurfaceObserver 对象的所需空间映射的数据空间的每个应用程序定义的区域。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="e4bb6-147">指定每个 SurfaceObserver 对象将通过调用 SetVolumeAsSphere、 SetVolumeAsAxisAlignedBox、 SetVolumeAsOrientedBox 或 SetVolumeAsFrustum 提供数据的空间的区域。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="e4bb6-148">可以通过只需调用这些方法之一来重新定义的空间在将来的区域。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="e4bb6-149">当调用 SurfaceObserver.Update() 时，必须提供 SurfaceObserver 的区域的空间映射系统具有的新信息的空间中每个空间表面一个处理程序。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="e4bb6-150">为一个空间表面接收处理程序：</span><span class="sxs-lookup"><span data-stu-id="e4bb6-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="e4bb6-151">处理图面上的更改</span><span class="sxs-lookup"><span data-stu-id="e4bb6-151">Handling Surface Changes</span></span>

<span data-ttu-id="e4bb6-152">有几个主要的情况下，若要处理。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-152">There are several main cases to handle.</span></span> <span data-ttu-id="e4bb6-153">添加和更新其可以使用相同的代码路径并将其删除。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="e4bb6-154">在示例中已添加和更新情况下，我们将添加或获取 GameObject 表示，这从字典 mesh、 SurfaceData 结构创建使用所需的组件，然后调用 RequestMeshDataAsync 来填充网格数据 GameObject 和定位在场景中。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="e4bb6-155">中已删除的情况下，我们将删除从字典中表示此网格的 GameObject，并将其销毁。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

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

### <a name="handling-data-ready"></a><span data-ttu-id="e4bb6-156">处理数据就绪</span><span class="sxs-lookup"><span data-stu-id="e4bb6-156">Handling Data Ready</span></span>

<span data-ttu-id="e4bb6-157">OnDataReady 处理程序接收 SurfaceData 对象。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="e4bb6-158">WorldAnchor、 MeshFilter 和 （可选） 的 MeshCollider 对象，它包含反映相关联的空间表面的最新状态。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="e4bb6-159">（可选） 执行分析和/或[处理](spatial-mapping.md#mesh-processing)通过访问 MeshFilter 对象的网格成员的网格数据。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="e4bb6-160">呈现与最新的网格在空间面和 （可选） 将其用于物理冲突和 raycasts。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="e4bb6-161">请务必确认 SurfaceData 内容均不为 null。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="e4bb6-162">开始处理更新</span><span class="sxs-lookup"><span data-stu-id="e4bb6-162">Start processing on updates</span></span>

<span data-ttu-id="e4bb6-163">SurfaceObserver.Update() 应该调用延迟，并非每个帧。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="e4bb6-164">更高级别的网格分析：SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="e4bb6-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="e4bb6-165"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>是 holographic 开发基于全息版的 Unity Api 有用实用工具代码的集合。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="e4bb6-166">空间了解</span><span class="sxs-lookup"><span data-stu-id="e4bb6-166">Spatial Understanding</span></span>

<span data-ttu-id="e4bb6-167">在现实环境中放置全息时是通常需要转超出空间映射网格图面平面。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="e4bb6-168">完成放置后按，更高级别的环境了解最好。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="e4bb6-169">这通常需要决定什么 floor、 ceiling 和墙。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="e4bb6-170">此外，针对到确定 holographic 对象最理想的物理位置的放置约束的一组优化的能力。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="e4bb6-171">在开发期间的 Young Conker 和片段，Asobo Studios 遇到此问题头上，为此开发聊天室解算器。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="e4bb6-172">每个这些游戏具有游戏的特定需求，但它们会共享核心空间了解技术。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="e4bb6-173">库封装这项技术，允许您快速查找在墙上上限，将对象置于空白空间标识 HoloToolkit.SpatialUnderstanding 放置要坐下来，字符和大量其他空间了解查询的时间。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="e4bb6-174">所有是源代码的包括在内，从而可以根据需求进行自定义和与社区共享您的改进。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="e4bb6-175">代码C++包装到 UWP dll 解算器和将其公开到 Unity 中 MixedRealityToolkit 包含预设中会显示下拉。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="e4bb6-176">了解模块</span><span class="sxs-lookup"><span data-stu-id="e4bb6-176">Understanding Modules</span></span>

<span data-ttu-id="e4bb6-177">有三个模块公开的主接口： 简单的图面和空间查询、 对象检测的形状和对象放置解算器用于约束基于放置的对象集的拓扑。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="e4bb6-178">下面描述了其中每项功能。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-178">Each of these is described below.</span></span> <span data-ttu-id="e4bb6-179">除了三个主模块接口，ray 强制转换接口可用于检索标记的图面类型和自定义的那样严密 playspace 网格可以复制出来。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="e4bb6-180">Ray 强制转换</span><span class="sxs-lookup"><span data-stu-id="e4bb6-180">Ray Casting</span></span>

<span data-ttu-id="e4bb6-181">聊天室已经过扫描并完成后，标签会在内部生成对于 floor、 ceiling 和墙等的图面。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="e4bb6-182">"PlayspaceRaycast"函数使用一条射线并返回如果射线与已知的图面有冲突，如果是这样，该图面中的"RaycastResult"窗体有关的信息。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

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

<span data-ttu-id="e4bb6-183">在内部，raycast 计算针对 playspace 的立方计算 8 cm voxel 表示形式。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="e4bb6-184">每个 voxel 包含一组的图面上元素与处理的拓扑数据 (也称为 surfels)。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="e4bb6-185">包含在相交的 voxel 单元格中 surfels 进行比较，用于查看拓扑信息的最佳匹配项。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="e4bb6-186">此拓扑的数据包含标记返回"SurfaceTypes"枚举的窗体以及相交曲面的图面区域。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="e4bb6-187">在 Unity 示例中，游标将一条转换为每个帧。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="e4bb6-188">首先，对 Unity 的碰撞体。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="e4bb6-189">其次，对了解模块的世界表示形式。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="e4bb6-190">和最后，再次 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-190">And finally, again UI elements.</span></span> <span data-ttu-id="e4bb6-191">在此应用程序中，UI 将获取优先级，接下来了解结果和最后，Unity 的碰撞体。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="e4bb6-192">SurfaceType 被报告为旁的文本。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="e4bb6-193">![图面上的类型标记旁](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4bb6-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="e4bb6-194">*图面上的类型标记旁*</span><span class="sxs-lookup"><span data-stu-id="e4bb6-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="e4bb6-195">拓扑查询</span><span class="sxs-lookup"><span data-stu-id="e4bb6-195">Topology Queries</span></span>

<span data-ttu-id="e4bb6-196">在 DLL 内的拓扑管理器处理环境的标记。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="e4bb6-197">如上所述，surfels，包含在 voxel 卷中存储的大量数据。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="e4bb6-198">此外，"PlaySpaceInfos"结构用于存储有关 playspace，包括世界对齐方式 （下文更多详细信息）、 floor、 和 ceiling 高度信息。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="e4bb6-199">启发式方法用于确定 floor、 ceiling 和墙。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="e4bb6-200">例如，与大于 1 m2 图面区域的最大和最小水平的面被视为基底。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="e4bb6-201">请注意在此过程中还使用在扫描过程中的照相机路径。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="e4bb6-202">公开的拓扑结构管理器的查询的子集通过 dll 公开出。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="e4bb6-203">公开的拓扑查询如下所示。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="e4bb6-204">每个查询具有一组特定的查询类型参数。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="e4bb6-205">在以下示例中，用户指定的最小高度和宽度的所需的卷、 更高版本的基底，最少的许可卷的前面放置最小高度。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="e4bb6-206">所有度量值是以米为单位。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="e4bb6-207">每个这些查询采用"TopologyResult"结构的预先分配的数组。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="e4bb6-208">"LocationCount"参数指定传入的数组的长度。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="e4bb6-209">返回值将报告返回位置数。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="e4bb6-210">此数字大于永远不会传递"locationCount"参数中。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="e4bb6-211">"TopologyResult"包含返回的卷、 面向公众的方向 （即正常），并找到空间的维度的中间位置。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="e4bb6-212">请注意，在 Unity 示例，这些查询的每个虚拟用户界面面板中的按钮为链接。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="e4bb6-213">硬示例代码的合理值到这些查询每个参数。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="e4bb6-214">有关更多示例的示例代码中看到 SpaceVisualizer.cs。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="e4bb6-215">形状的查询</span><span class="sxs-lookup"><span data-stu-id="e4bb6-215">Shape Queries</span></span>

<span data-ttu-id="e4bb6-216">在 dll 内形状分析器 ("ShapeAnalyzer_W") 使用拓扑分析器来匹配由用户定义的自定义形状。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="e4bb6-217">Unity 示例定义了一组形状，并公开应用程序内查询菜单上的形状选项卡中，通过输出结果。目的是用户可以定义自己对象的形状查询并使其应用程序所需的使用。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="e4bb6-218">请注意，形状 analysis 工作仅水平图面上。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="e4bb6-219">躺椅，例如，是由平面席位面和平面顶部躺椅上重新定义。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="e4bb6-220">Shape 查询查找与两个表面对齐和连接特定大小、 高度和长宽范围的两个面。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="e4bb6-221">使用 Api 术语，couch 席位和后顶部是形状的组件和对齐要求是形状组件的约束。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="e4bb6-222">在 Unity 示例 (ShapeDefinition.cs) 中为"sittable"对象定义的示例查询如下所示。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

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

<span data-ttu-id="e4bb6-223">每个 shape 查询由一组形状组件，每个都有一组组件约束和一组形状约束定义其列出的组件之间的依赖项。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="e4bb6-224">（因为只有一个组件），此示例在单个组件定义和组件之间的任何形状约束中包含三个约束。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="e4bb6-225">与此相反，couch 形状具有两个形状组件和四个形状约束。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="e4bb6-226">请注意，由它们在用户的组件列表 （0 和 1 在此示例中） 中的索引标识组件。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="e4bb6-227">轻松创建自定义形状定义 Unity 模块中提供了包装器函数。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="e4bb6-228">可以在"ShapeComponentConstraint"和"ShapeConstraint"结构"SpatialUnderstandingDll.cs"中找到的组件和形状的约束的完整列表。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="e4bb6-229">![此图面上找到矩形形状](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4bb6-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="e4bb6-230">*此图面上找到矩形形状*</span><span class="sxs-lookup"><span data-stu-id="e4bb6-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="e4bb6-231">对象放置解算器</span><span class="sxs-lookup"><span data-stu-id="e4bb6-231">Object Placement Solver</span></span>

<span data-ttu-id="e4bb6-232">对象放置解算器可以用于确定放置您的对象的物理空间中的理想位置。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="e4bb6-233">解算器将查找最适合给定的对象规则和约束的位置。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="e4bb6-234">此外，对象查询持续，直到使用"Solver_RemoveObject"中删除的对象或"Solver_RemoveAllObjects"调用，从而允许约束多重对象位置。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="e4bb6-235">对象放置查询由三部分组成： 参数、 一组规则，与约束的列表的位置类型。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="e4bb6-236">若要运行查询，使用以下 API。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-236">To run a query, use the following API.</span></span>

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

<span data-ttu-id="e4bb6-237">此函数采用对象名称、 位置定义和规则和约束的列表。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="e4bb6-238">C#包装器提供构造帮助器函数来简化规则和约束构造。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="e4bb6-239">放置定义包含查询类型 – 也就是说，以下值之一。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-239">The placement definition contains the query type – that is, one of the following.</span></span>

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

<span data-ttu-id="e4bb6-240">每个位置类型具有一组唯一的类型参数。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="e4bb6-241">"ObjectPlacementDefinition"结构包含一组用于创建这些定义的静态帮助器函数。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="e4bb6-242">例如，若要查找的地板上放置对象的地方，可以使用以下函数。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="e4bb6-243">公共静态 ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) 中添加到的位置类型，可以提供一组规则和约束。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="e4bb6-244">不能违反规则。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-244">Rules cannot be violated.</span></span> <span data-ttu-id="e4bb6-245">满足的类型和规则的可能的放置位置然后进行了优化针对的约束的集合，以便选择最佳的放置位置。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="e4bb6-246">提供静态创建函数，可以创建的每个规则和约束。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="e4bb6-247">下面提供了一个示例规则和约束构造函数。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="e4bb6-248">对象的下方放置查询将查找一个位置来图面的边缘放置一半计量多维数据集、 远离其他以前放置对象和中心附近的房间。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

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

<span data-ttu-id="e4bb6-249">如果成功，包含在中放置的位置的"ObjectPlacementResult"结构尺寸和方向返回。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="e4bb6-250">此外，位置被添加到放置对象的 dll 的内部列表。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="e4bb6-251">后续放置查询会考虑到此对象。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="e4bb6-252">Unity 示例中的"LevelSolver.cs"文件包含更多的示例查询。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="e4bb6-253">![结果的对象放置](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4bb6-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="e4bb6-254">*图 3:蓝色框如何地板上的三个位置，从结果查询与从照相机位置规则*</span><span class="sxs-lookup"><span data-stu-id="e4bb6-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="e4bb6-255">当解决所需的级别或应用程序方案的多个对象的放置位置，第一个解决到最大化可找到空间的概率的顺序不可或缺的大型对象。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="e4bb6-256">放置顺序非常重要。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-256">Placement order is important.</span></span> <span data-ttu-id="e4bb6-257">如果找不到对象位置，请尝试不太受约束的配置。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="e4bb6-258">具有一组的回退配置对跨多个空间配置支持的功能至关重要。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="e4bb6-259">聊天室扫描进程</span><span class="sxs-lookup"><span data-stu-id="e4bb6-259">Room Scanning Process</span></span>

<span data-ttu-id="e4bb6-260">虽然 HoloLens 由提供的空间映射解决方案专为一般性还不足以满足整个域中问题所在领域的需求，生成空间了解模块来支持这两个特定游戏的需求。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="e4bb6-261">其解决方案的结构围绕特定的进程和假设，总结如下。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="e4bb6-262">用户驱动的 playspace"绘制"– 在扫描阶段，用户将移动，并查找在播放上发展步伐，有效地进行绘制的区域应包括。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="e4bb6-263">务必在此阶段提供用户反馈是生成的网格。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="e4bb6-264">室内 home 或 office 设置 – 函数围绕平面曲面和墙成直角设计的查询。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="e4bb6-265">这是软限制。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-265">This is a soft limitation.</span></span> <span data-ttu-id="e4bb6-266">但是，在扫描阶段，主坐标轴分析完成优化主版本号和次的轴的网格分割。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="e4bb6-267">所包含的 SpatialUnderstanding.cs 文件管理扫描阶段的过程。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="e4bb6-268">它将调用以下函数。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-268">It calls the following functions.</span></span>

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

<span data-ttu-id="e4bb6-269">扫描的流，由"SpatialUnderstanding"行为驱动调用 InitScan，然后 UpdateScan 每个帧。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="e4bb6-270">当统计信息查询报告合理覆盖率时，允许用户为 airtap 调用 RequestFinish 指示扫描阶段结束。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="e4bb6-271">UpdateScan 继续调用之前返回值指示 dll 已完成处理。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="e4bb6-272">了解网格</span><span class="sxs-lookup"><span data-stu-id="e4bb6-272">Understanding Mesh</span></span>

<span data-ttu-id="e4bb6-273">了解 dll 在内部存储 playspace 为调整大小的 8 cm voxel 多维数据集的网格。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="e4bb6-274">在扫描的初始阶段，完成主成分分析以确定聊天室的轴。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="e4bb6-275">在内部，它将存储到这些轴对齐其 voxel 空间。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="e4bb6-276">通过从 voxel 卷提取等值面大约每隔一秒生成网格。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="e4bb6-277">![生成从 voxel 卷生成的网格](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4bb6-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="e4bb6-278">*生成从 voxel 卷生成的网格*</span><span class="sxs-lookup"><span data-stu-id="e4bb6-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e4bb6-279">疑难解答</span><span class="sxs-lookup"><span data-stu-id="e4bb6-279">Troubleshooting</span></span>
* <span data-ttu-id="e4bb6-280">确保已设置[SpatialPerception](#setting-the-spatialperception-capability)功能</span><span class="sxs-lookup"><span data-stu-id="e4bb6-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="e4bb6-281">丢失跟踪时下, 一步 OnSurfaceChanged 事件将删除所有网格。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="e4bb6-282">混合的现实工具包中的空间映射</span><span class="sxs-lookup"><span data-stu-id="e4bb6-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="e4bb6-283">与混合现实 Toolkit v2 使用空间映射的详细信息，请参阅<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">空间感知部分</a>MRTK docs。</span><span class="sxs-lookup"><span data-stu-id="e4bb6-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4bb6-284">请参阅</span><span class="sxs-lookup"><span data-stu-id="e4bb6-284">See also</span></span>
* [<span data-ttu-id="e4bb6-285">MR 空间 230:空间映射</span><span class="sxs-lookup"><span data-stu-id="e4bb6-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="e4bb6-286">坐标系统</span><span class="sxs-lookup"><span data-stu-id="e4bb6-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="e4bb6-287">在 Unity 中的坐标系统</span><span class="sxs-lookup"><span data-stu-id="e4bb6-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="e4bb6-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="e4bb6-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="e4bb6-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="e4bb6-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="e4bb6-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="e4bb6-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="e4bb6-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="e4bb6-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
