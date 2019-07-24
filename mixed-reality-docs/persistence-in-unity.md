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
# <a name="persistence-in-unity"></a>Unity 中的持久性

**命名空间：** *UnityEngine. XR*<br>
**类：**  *WorldAnchorStore*

WorldAnchorStore 是创建全息体验的关键, 其中全息在应用程序的实例上保持特定的实际位置。 这样, 用户就可以在任何需要的位置固定各个全息影像或工作区, 然后在以后发现应用的许多用途时找到它。

## <a name="how-to-persist-holograms-across-sessions"></a>如何跨会话保留全息影像

WorldAnchorStore 可让你在不同的会话中持久保存 WorldAnchor 的位置。 若要在会话中实际保留全息影像, 需要单独跟踪使用特定世界锚点的 Gameobject。 通常, 使用世界定位点创建 GameObject 根是有意义的, 并使子影像由其定位到本地位置偏移量。

从以前的会话加载全息影像:
1. 获取 WorldAnchorStore
2. 加载与世界定位点相关的应用数据, 提供世界锚的 id
3. 从其 id 加载世界定位点

为将来的会话保存全息影像:
1. 获取 WorldAnchorStore
2. 保存指定 id 的世界定位点
3. 保存与世界锚点相关的应用数据以及 id

### <a name="getting-the-worldanchorstore"></a>获取 WorldAnchorStore

我们想要保存对 WorldAnchorStore 的引用, 以便我们知道我们在要执行某个操作时准备好了。 由于这是一个异步调用, 可能很快就会启动, 我们想要调用

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

在此示例中, StoreLoaded 是 WorldAnchorStore 完成加载时的处理程序:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

现在, 我们对 WorldAnchorStore 的引用, 我们将使用它来保存和加载特定世界锚。

### <a name="saving-a-worldanchor"></a>保存 WorldAnchor

若要保存, 只需命名要保存的内容, 并将其传递到 WorldAnchor 我们要保存的时间。 注意: 尝试将两个定位点保存到同一个字符串会失败 (存储。保存将返回 false)。 保存新的保存之前, 需要先删除以前的保存:

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

### <a name="loading-a-worldanchor"></a>加载 WorldAnchor

并加载:

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

我们还可以使用 store。删除 () 以删除以前保存和存储的定位点。清除 () 以删除以前保存的所有数据。

### <a name="enumerating-existing-anchors"></a>枚举现有锚

若要发现以前存储的定位点, 请调用 GetAllIds。

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>为多台设备保留全息影像

你可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a>从本地 WorldAnchor 创建持久的云锚点, 你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找, 即使这些设备同时不存在。  由于云锚点是永久性的, 随着时间的推移, 多台设备可以看到相对于同一物理位置中的定位点呈现的内容。

若要开始在 Unity 中构建共享体验, 请尝试执行5分钟的<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。

启动并运行 Azure 空间锚点后, 便可以<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。

## <a name="see-also"></a>请参阅
* [空间锚点持久性](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a>
