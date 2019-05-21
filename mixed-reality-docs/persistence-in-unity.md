---
title: 在 Unity 中的暂留
description: 持久性，您的任意位置，然后再查找它更高版本，他们希望通过许多使用您的应用程序的固定单个全息或工作区的用户。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens，暂留，Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593063"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="64ff9-104">在 Unity 中的暂留</span><span class="sxs-lookup"><span data-stu-id="64ff9-104">Persistence in Unity</span></span>

<span data-ttu-id="64ff9-105">**命名空间：** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="64ff9-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="64ff9-106">**类：**  *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="64ff9-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="64ff9-107">WorldAnchorStore 是创建全息版体验的关键位置全息处于特定实际位置跨应用程序的实例。</span><span class="sxs-lookup"><span data-stu-id="64ff9-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="64ff9-108">这样，你的用户固定单个全息或工作区，无论他们所需，，然后找到它更高版本，他们希望通过您的应用程序的许多用途。</span><span class="sxs-lookup"><span data-stu-id="64ff9-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="64ff9-109">如何在会话之间持久保存全息</span><span class="sxs-lookup"><span data-stu-id="64ff9-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="64ff9-110">WorldAnchorStore 将允许你保留在不同的会话的 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="64ff9-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="64ff9-111">实际上在会话之间持久保存全息，将需要单独跟踪的应用使用特定的全球定位点的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="64ff9-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="64ff9-112">通常最好使用全球定位点创建 GameObject 根和具有子级全息定位由它具有本地位置的偏移量。</span><span class="sxs-lookup"><span data-stu-id="64ff9-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="64ff9-113">若要从以前的会话中加载全息：</span><span class="sxs-lookup"><span data-stu-id="64ff9-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="64ff9-114">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="64ff9-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="64ff9-115">加载与世界上的定位点，它为您提供了世界锚点 id 相关的应用程序数据</span><span class="sxs-lookup"><span data-stu-id="64ff9-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="64ff9-116">从其 id 加载世界定位点</span><span class="sxs-lookup"><span data-stu-id="64ff9-116">Load a world anchor from its id</span></span>

<span data-ttu-id="64ff9-117">若要将全息另存为将来的会话：</span><span class="sxs-lookup"><span data-stu-id="64ff9-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="64ff9-118">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="64ff9-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="64ff9-119">保存指定 id 的世界锚点</span><span class="sxs-lookup"><span data-stu-id="64ff9-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="64ff9-120">保存与世界锚点 id 以及相关的应用程序数据</span><span class="sxs-lookup"><span data-stu-id="64ff9-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="64ff9-121">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="64ff9-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="64ff9-122">我们想要保留对周围 WorldAnchorStore 的引用，因此我们知道我们是准备就绪时我们想要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="64ff9-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="64ff9-123">由于这是一个异步调用，可能会尽快开始，我们希望调用</span><span class="sxs-lookup"><span data-stu-id="64ff9-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="64ff9-124">StoreLoaded 这种情况下是 WorldAnchorStore 在完成加载后的我们处理程序：</span><span class="sxs-lookup"><span data-stu-id="64ff9-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="64ff9-125">现在，我们对 WorldAnchorStore 我们将用来保存和加载特定的全球定位点的引用。</span><span class="sxs-lookup"><span data-stu-id="64ff9-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="64ff9-126">正在保存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="64ff9-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="64ff9-127">若要保存，我们只需命名为我们要保存并将其传递我们之前获得想要保存的 WorldAnchor 中。</span><span class="sxs-lookup"><span data-stu-id="64ff9-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="64ff9-128">请注意： 尝试将两个定位点保存到相同的字符串会失败 （应用商店。保存将返回 false）。</span><span class="sxs-lookup"><span data-stu-id="64ff9-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="64ff9-129">您需要删除以前保存新之前保存：</span><span class="sxs-lookup"><span data-stu-id="64ff9-129">You need to Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="64ff9-130">正在加载 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="64ff9-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="64ff9-131">和加载：</span><span class="sxs-lookup"><span data-stu-id="64ff9-131">And to load:</span></span>

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

<span data-ttu-id="64ff9-132">此外，我们可以使用应用商店。Delete （） 若要删除我们以前保存的定位点和应用商店。Clear （) 以删除所有以前保存的数据。</span><span class="sxs-lookup"><span data-stu-id="64ff9-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="64ff9-133">枚举现有的定位点</span><span class="sxs-lookup"><span data-stu-id="64ff9-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="64ff9-134">若要发现以前存储的定位点，请调用 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="64ff9-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="64ff9-135">保存全息适用于多个设备</span><span class="sxs-lookup"><span data-stu-id="64ff9-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="64ff9-136">可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间的定位点</a>从您的应用程序可以然后找到跨多个 HoloLens、 iOS 和 Android 设备，即使这些设备不存在同时在同一本地 WorldAnchor 创建持久的云定位点时间。</span><span class="sxs-lookup"><span data-stu-id="64ff9-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="64ff9-137">云定位标记是持久的因为随着时间的推移的多个设备每个所见内容呈现相对于同一物理位置中的定位点。</span><span class="sxs-lookup"><span data-stu-id="64ff9-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="64ff9-138">若要开始构建在 Unity 中的共享的体验，请尝试出 5 分钟<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">快速入门 Azure 空间的定位点 Unity</a>。</span><span class="sxs-lookup"><span data-stu-id="64ff9-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="64ff9-139">你可以在 Azure 空间的定位点与您使用启动并运行，然后<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">创建并在 Unity 中定位的定位点</a>。</span><span class="sxs-lookup"><span data-stu-id="64ff9-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="64ff9-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="64ff9-140">See Also</span></span>
* [<span data-ttu-id="64ff9-141">空间定位点暂留</span><span class="sxs-lookup"><span data-stu-id="64ff9-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="64ff9-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a></span><span class="sxs-lookup"><span data-stu-id="64ff9-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="64ff9-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空间的定位点适用于 Unity SDK</a></span><span class="sxs-lookup"><span data-stu-id="64ff9-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
