---
title: Unity 中的本地定位点传输
description: 在 Unity 应用程序中的多个 HoloLens 设备之间传输定位点。
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: 共享、定位、WorldAnchor、MR 共享250、WorldAnchorTransferBatch、SpatialPerception、传输、本地定位点传输、定位点导出和定位点导入
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516135"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="494b8-104">Unity 中的本地定位点传输</span><span class="sxs-lookup"><span data-stu-id="494b8-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="494b8-105">在不能使用<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间锚点</a>的情况下, 本地定位点传输允许一台 hololens 设备导出要由第二个 hololens 设备导入的定位点。</span><span class="sxs-lookup"><span data-stu-id="494b8-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="494b8-106">与<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位</a>点相比, 本地定位点传输提供的功能更低, 并且不支持 IOS 和 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="494b8-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="494b8-107">设置 SpatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="494b8-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="494b8-108">为了使应用能够传输空间锚, 必须启用*SpatialPerception*功能。</span><span class="sxs-lookup"><span data-stu-id="494b8-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="494b8-109">如何启用*SpatialPerception*功能:</span><span class="sxs-lookup"><span data-stu-id="494b8-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="494b8-110">在 Unity 编辑器中, 打开 **"播放机设置"** 窗格 (编辑 > Player > 项目设置)</span><span class="sxs-lookup"><span data-stu-id="494b8-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="494b8-111">单击 **"Windows 应用商店"** 选项卡</span><span class="sxs-lookup"><span data-stu-id="494b8-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="494b8-112">展开 **"发布设置"** , 然后在 **"功能"** 列表中检查 **"SpatialPerception"** 功能</span><span class="sxs-lookup"><span data-stu-id="494b8-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="494b8-113">如果已将 Unity 项目导出到 Visual Studio 解决方案, 则需要导出到新文件夹或[在 Visual studio 的 appxmanifest.xml 中手动设置此功能](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。</span><span class="sxs-lookup"><span data-stu-id="494b8-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="494b8-114">定位点传输</span><span class="sxs-lookup"><span data-stu-id="494b8-114">Anchor Transfer</span></span>

<span data-ttu-id="494b8-115">**命名空间：**  *UnityEngine.XR.WSA.Sharing*</span><span class="sxs-lookup"><span data-stu-id="494b8-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="494b8-116">类型：*WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="494b8-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="494b8-117">若要传输[WorldAnchor](coordinate-systems-in-unity.md), 必须建立要传输的定位点。</span><span class="sxs-lookup"><span data-stu-id="494b8-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="494b8-118">一个 HoloLens 的用户将扫描其环境, 并手动或以编程方式选择空间中的一个点作为共享体验的定位点。</span><span class="sxs-lookup"><span data-stu-id="494b8-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="494b8-119">然后, 可以对表示此点的数据进行序列化, 并将其传输到在体验中共享的其他设备。</span><span class="sxs-lookup"><span data-stu-id="494b8-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="494b8-120">然后, 每个设备会反序列化定位点数据, 并尝试在空间中查找该点。</span><span class="sxs-lookup"><span data-stu-id="494b8-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="494b8-121">为了使定位点传输正常工作, 每个设备都必须扫描足够多的环境, 以便可以标识定位点表示的点。</span><span class="sxs-lookup"><span data-stu-id="494b8-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="494b8-122">安装</span><span class="sxs-lookup"><span data-stu-id="494b8-122">Setup</span></span>

<span data-ttu-id="494b8-123">此页上的示例代码中有几个字段需要初始化:</span><span class="sxs-lookup"><span data-stu-id="494b8-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="494b8-124">*GameObject rootGameObject*是 Unity 中的*GameObject* , 其中包含*WorldAnchor*组件。</span><span class="sxs-lookup"><span data-stu-id="494b8-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="494b8-125">共享体验中的一个用户会将此*GameObject* , 并将数据导出到其他用户。</span><span class="sxs-lookup"><span data-stu-id="494b8-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="494b8-126">*WorldAnchor gameRootAnchor*是位于*WorldAnchor*上的*UnityEngine。*</span><span class="sxs-lookup"><span data-stu-id="494b8-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="494b8-127">*byte [] importedData*是每个客户端通过网络接收的序列化定位点的字节数组。</span><span class="sxs-lookup"><span data-stu-id="494b8-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a><span data-ttu-id="494b8-128">输出</span><span class="sxs-lookup"><span data-stu-id="494b8-128">Exporting</span></span>

<span data-ttu-id="494b8-129">若要导出, 我们只需要一个*WorldAnchor* , 并了解我们将对其进行调用, 使接收应用有意义。</span><span class="sxs-lookup"><span data-stu-id="494b8-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="494b8-130">共享体验中的一个客户端将执行以下步骤以导出共享锚:</span><span class="sxs-lookup"><span data-stu-id="494b8-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="494b8-131">创建*WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="494b8-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="494b8-132">添加要传输的*WorldAnchors*</span><span class="sxs-lookup"><span data-stu-id="494b8-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="494b8-133">开始导出</span><span class="sxs-lookup"><span data-stu-id="494b8-133">Begin the export</span></span>
4. <span data-ttu-id="494b8-134">在数据变为可用时处理*OnExportDataAvailable*事件</span><span class="sxs-lookup"><span data-stu-id="494b8-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="494b8-135">处理*OnExportComplete*事件</span><span class="sxs-lookup"><span data-stu-id="494b8-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="494b8-136">我们会创建一个*WorldAnchorTransferBatch*来封装要传输的内容, 然后将其导出到字节:</span><span class="sxs-lookup"><span data-stu-id="494b8-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="494b8-137">数据变得可用时, 将字节作为数据段发送到客户端或缓冲区, 并通过任何所需的方法发送:</span><span class="sxs-lookup"><span data-stu-id="494b8-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="494b8-138">导出完成后, 如果我们已传输数据并且序列化失败, 请告知客户端丢弃数据。</span><span class="sxs-lookup"><span data-stu-id="494b8-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="494b8-139">如果序列化成功, 请告知客户端所有数据都已传输并可以开始导入:</span><span class="sxs-lookup"><span data-stu-id="494b8-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a><span data-ttu-id="494b8-140">导入</span><span class="sxs-lookup"><span data-stu-id="494b8-140">Importing</span></span>

<span data-ttu-id="494b8-141">接收到发送方发来的所有字节后, 可以将数据导入回*WorldAnchorTransferBatch* , 并将根游戏对象锁定到相同的物理位置。</span><span class="sxs-lookup"><span data-stu-id="494b8-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="494b8-142">注意: 有时 transiently 会失败, 需要重试:</span><span class="sxs-lookup"><span data-stu-id="494b8-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

<span data-ttu-id="494b8-143">通过*LockObject*调用锁定*GameObject*后, 它将具有一个*WorldAnchor* , 它会将其保持在世界上相同的物理位置, 但它可能与其他用户在 Unity 坐标空间中的位置不同。</span><span class="sxs-lookup"><span data-stu-id="494b8-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

