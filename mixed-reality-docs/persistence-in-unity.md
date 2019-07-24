---
title: Unity 中的持久性
description: 通过使用持久性, 你的用户可以根据需要在任何位置固定单个全息影像或工作区, 然后在以后发现应用的许多用途时找到它。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、暂留、Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524786"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="1254a-104">Unity 中的持久性</span><span class="sxs-lookup"><span data-stu-id="1254a-104">Persistence in Unity</span></span>

<span data-ttu-id="1254a-105">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="1254a-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="1254a-106">**类：**  *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="1254a-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="1254a-107">WorldAnchorStore 是创建全息体验的关键, 其中全息在应用程序的实例上保持特定的实际位置。</span><span class="sxs-lookup"><span data-stu-id="1254a-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="1254a-108">这样, 用户就可以在任何需要的位置固定各个全息影像或工作区, 然后在以后发现应用的许多用途时找到它。</span><span class="sxs-lookup"><span data-stu-id="1254a-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="1254a-109">如何跨会话保留全息影像</span><span class="sxs-lookup"><span data-stu-id="1254a-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="1254a-110">WorldAnchorStore 可让你在不同的会话中持久保存 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="1254a-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="1254a-111">若要在会话中实际保留全息影像, 需要单独跟踪使用特定世界锚点的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="1254a-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="1254a-112">通常, 使用世界定位点创建 GameObject 根是有意义的, 并使子影像由其定位到本地位置偏移量。</span><span class="sxs-lookup"><span data-stu-id="1254a-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="1254a-113">从以前的会话加载全息影像:</span><span class="sxs-lookup"><span data-stu-id="1254a-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="1254a-114">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="1254a-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="1254a-115">加载与世界定位点相关的应用数据, 提供世界锚的 id</span><span class="sxs-lookup"><span data-stu-id="1254a-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="1254a-116">从其 id 加载世界定位点</span><span class="sxs-lookup"><span data-stu-id="1254a-116">Load a world anchor from its id</span></span>

<span data-ttu-id="1254a-117">为将来的会话保存全息影像:</span><span class="sxs-lookup"><span data-stu-id="1254a-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="1254a-118">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="1254a-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="1254a-119">保存指定 id 的世界定位点</span><span class="sxs-lookup"><span data-stu-id="1254a-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="1254a-120">保存与世界锚点相关的应用数据以及 id</span><span class="sxs-lookup"><span data-stu-id="1254a-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="1254a-121">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="1254a-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="1254a-122">我们想要保存对 WorldAnchorStore 的引用, 以便我们知道我们在要执行某个操作时准备好了。</span><span class="sxs-lookup"><span data-stu-id="1254a-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="1254a-123">由于这是一个异步调用, 可能很快就会启动, 我们想要调用</span><span class="sxs-lookup"><span data-stu-id="1254a-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="1254a-124">在此示例中, StoreLoaded 是 WorldAnchorStore 完成加载时的处理程序:</span><span class="sxs-lookup"><span data-stu-id="1254a-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="1254a-125">现在, 我们对 WorldAnchorStore 的引用, 我们将使用它来保存和加载特定世界锚。</span><span class="sxs-lookup"><span data-stu-id="1254a-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="1254a-126">保存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="1254a-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="1254a-127">若要保存, 只需命名要保存的内容, 并将其传递到 WorldAnchor 我们要保存的时间。</span><span class="sxs-lookup"><span data-stu-id="1254a-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="1254a-128">注意: 尝试将两个定位点保存到同一个字符串会失败 (存储。保存将返回 false)。</span><span class="sxs-lookup"><span data-stu-id="1254a-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="1254a-129">保存新的保存之前, 需要先删除以前的保存:</span><span class="sxs-lookup"><span data-stu-id="1254a-129">You need to Delete the previous save before saving the new one:</span></span>

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="1254a-130">加载 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="1254a-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="1254a-131">并加载:</span><span class="sxs-lookup"><span data-stu-id="1254a-131">And to load:</span></span>

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

<span data-ttu-id="1254a-132">我们还可以使用 store。删除 () 以删除以前保存和存储的定位点。清除 () 以删除以前保存的所有数据。</span><span class="sxs-lookup"><span data-stu-id="1254a-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="1254a-133">枚举现有锚</span><span class="sxs-lookup"><span data-stu-id="1254a-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="1254a-134">若要发现以前存储的定位点, 请调用 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="1254a-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="1254a-135">为多台设备保留全息影像</span><span class="sxs-lookup"><span data-stu-id="1254a-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="1254a-136">你可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a>从本地 WorldAnchor 创建持久的云锚点, 你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找, 即使这些设备同时不存在。</span><span class="sxs-lookup"><span data-stu-id="1254a-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="1254a-137">由于云锚点是永久性的, 随着时间的推移, 多台设备可以看到相对于同一物理位置中的定位点呈现的内容。</span><span class="sxs-lookup"><span data-stu-id="1254a-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="1254a-138">若要开始在 Unity 中构建共享体验, 请尝试执行5分钟的<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。</span><span class="sxs-lookup"><span data-stu-id="1254a-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="1254a-139">启动并运行 Azure 空间锚点后, 便可以<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。</span><span class="sxs-lookup"><span data-stu-id="1254a-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="1254a-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="1254a-140">See Also</span></span>
* [<span data-ttu-id="1254a-141">空间锚点持久性</span><span class="sxs-lookup"><span data-stu-id="1254a-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="1254a-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a></span><span class="sxs-lookup"><span data-stu-id="1254a-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="1254a-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a></span><span class="sxs-lookup"><span data-stu-id="1254a-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
