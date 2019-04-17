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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593063"
---
# <a name="persistence-in-unity"></a>在 Unity 中的暂留

**命名空间：***UnityEngine.XR.WSA.Persistence*<br>
**类：***WorldAnchorStore*

WorldAnchorStore 是创建全息版体验的关键位置全息处于特定实际位置跨应用程序的实例。 这样，你的用户固定单个全息或工作区，无论他们所需，，然后找到它更高版本，他们希望通过您的应用程序的许多用途。

## <a name="how-to-persist-holograms-across-sessions"></a>如何在会话之间持久保存全息

WorldAnchorStore 将允许你保留在不同的会话的 WorldAnchor 的位置。 实际上在会话之间持久保存全息，将需要单独跟踪的应用使用特定的全球定位点的 Gameobject。 通常最好使用全球定位点创建 GameObject 根和具有子级全息定位由它具有本地位置的偏移量。

若要从以前的会话中加载全息：
1. 获取 WorldAnchorStore
2. 加载与世界上的定位点，它为您提供了世界锚点 id 相关的应用程序数据
3. 从其 id 加载世界定位点

若要将全息另存为将来的会话：
1. 获取 WorldAnchorStore
2. 保存指定 id 的世界锚点
3. 保存与世界锚点 id 以及相关的应用程序数据

### <a name="getting-the-worldanchorstore"></a>获取 WorldAnchorStore

我们想要保留对周围 WorldAnchorStore 的引用，因此我们知道我们是准备就绪时我们想要执行的操作。 由于这是一个异步调用，可能会尽快开始，我们希望调用

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded 这种情况下是 WorldAnchorStore 在完成加载后的我们处理程序：

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

现在，我们对 WorldAnchorStore 我们将用来保存和加载特定的全球定位点的引用。

### <a name="saving-a-worldanchor"></a>正在保存 WorldAnchor

若要保存，我们只需命名为我们要保存并将其传递我们之前获得想要保存的 WorldAnchor 中。 请注意： 尝试将两个定位点保存到相同的字符串会失败 （应用商店。保存将返回 false）。 您需要删除以前保存新之前保存：

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

### <a name="loading-a-worldanchor"></a>正在加载 WorldAnchor

和加载：

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

此外，我们可以使用应用商店。Delete （） 若要删除我们以前保存的定位点和应用商店。Clear （) 以删除所有以前保存的数据。

### <a name="enumerating-existing-anchors"></a>枚举现有的定位点

若要发现以前存储的定位点，请调用 GetAllIds。

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>保存全息适用于多个设备

可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间的定位点</a>从您的应用程序可以然后找到跨多个 HoloLens、 iOS 和 Android 设备，即使这些设备不存在同时在同一本地 WorldAnchor 创建持久的云定位点时间。  云定位标记是持久的因为随着时间的推移的多个设备每个所见内容呈现相对于同一物理位置中的定位点。

若要开始构建在 Unity 中的共享的体验，请尝试出 5 分钟<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">快速入门 Azure 空间的定位点 Unity</a>。

你可以在 Azure 空间的定位点与您使用启动并运行，然后<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">创建并在 Unity 中定位的定位点</a>。

## <a name="see-also"></a>请参阅
* [空间定位点暂留](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空间的定位点适用于 Unity SDK</a>
