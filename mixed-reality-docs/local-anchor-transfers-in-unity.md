---
title: 在 Unity 中的本地定位点传输
description: 在 Unity 应用程序中的多个 HoloLens 设备之间传输的定位点。
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: 共享、 定位、 WorldAnchor、 MR 共享 250、 WorldAnchorTransferBatch、 SpatialPerception、 传输、 本地定位点传输、 定位点导出、 定位点导入
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593059"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="c613f-104">在 Unity 中的本地定位点传输</span><span class="sxs-lookup"><span data-stu-id="c613f-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="c613f-105">在不能使用情况下<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a>，本地的定位点传输启用一个 HoloLens 设备导出要导入第二个 HoloLens 设备的定位点。</span><span class="sxs-lookup"><span data-stu-id="c613f-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="c613f-106">本地的定位点复制提供了比更不稳定的定位点召回<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a>，以及 iOS 和 Android 设备不支持这种方法。</span><span class="sxs-lookup"><span data-stu-id="c613f-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="c613f-107">设置 SpatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="c613f-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="c613f-108">为了使应用程序传输空间定位点*SpatialPerception*必须启用功能。</span><span class="sxs-lookup"><span data-stu-id="c613f-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="c613f-109">如何启用*SpatialPerception*功能：</span><span class="sxs-lookup"><span data-stu-id="c613f-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="c613f-110">在 Unity 编辑器中打开 **"播放器设置"** 窗格 (编辑 > 项目设置 > 播放机)</span><span class="sxs-lookup"><span data-stu-id="c613f-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="c613f-111">单击 **"Windows 应用商店"** 选项卡</span><span class="sxs-lookup"><span data-stu-id="c613f-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="c613f-112">展开 **"发布设置"** ，并检查 **"SpatialPerception"** 中的功能 **"功能"** 列表</span><span class="sxs-lookup"><span data-stu-id="c613f-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="c613f-113">如果你已向 Visual Studio 解决方案导出你的 Unity 项目，你将需要导出到新文件夹或手动[在 Visual Studio 中的 AppxManifest 中设置此功能](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。</span><span class="sxs-lookup"><span data-stu-id="c613f-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="c613f-114">定位点传输</span><span class="sxs-lookup"><span data-stu-id="c613f-114">Anchor Transfer</span></span>

<span data-ttu-id="c613f-115">**命名空间：**  *UnityEngine.XR.WSA.Sharing*</span><span class="sxs-lookup"><span data-stu-id="c613f-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="c613f-116">类型：*WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="c613f-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="c613f-117">要传输[WorldAnchor](coordinate-systems-in-unity.md)，其中一个必须建立要传输的定位点。</span><span class="sxs-lookup"><span data-stu-id="c613f-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="c613f-118">一个 HoloLens 用户扫描其环境，并手动或以编程方式为共享体验的定位点的空间中选择一个点。</span><span class="sxs-lookup"><span data-stu-id="c613f-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="c613f-119">然后，将表示此点的数据序列化并将其传输到体验中共享的其他设备。</span><span class="sxs-lookup"><span data-stu-id="c613f-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="c613f-120">每个设备然后反序列化的定位点数据，并尝试在空间中找到该点。</span><span class="sxs-lookup"><span data-stu-id="c613f-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="c613f-121">为了使定位点传输工作，必须具有每个设备扫描中足够多的环境，以便可以标识定位标记所表示的点。</span><span class="sxs-lookup"><span data-stu-id="c613f-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="c613f-122">安装</span><span class="sxs-lookup"><span data-stu-id="c613f-122">Setup</span></span>

<span data-ttu-id="c613f-123">此页上的示例代码具有几个字段，将需要进行初始化：</span><span class="sxs-lookup"><span data-stu-id="c613f-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="c613f-124">*GameObject rootGameObject*是*GameObject*在 Unity 中具有*WorldAnchor*组件在其上。</span><span class="sxs-lookup"><span data-stu-id="c613f-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="c613f-125">中的共享体验的一个用户会将这*GameObject*和将数据导出到其他用户。</span><span class="sxs-lookup"><span data-stu-id="c613f-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="c613f-126">*WorldAnchor gameRootAnchor*是*UnityEngine.XR.WSA.WorldAnchor*这也是*rootGameObject*。</span><span class="sxs-lookup"><span data-stu-id="c613f-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="c613f-127">*字节 [] importedData*是序列化的定位点在网络上接收每个客户端的字节数组。</span><span class="sxs-lookup"><span data-stu-id="c613f-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

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

### <a name="exporting"></a><span data-ttu-id="c613f-128">导出</span><span class="sxs-lookup"><span data-stu-id="c613f-128">Exporting</span></span>

<span data-ttu-id="c613f-129">若要导出，我们只需*WorldAnchor*并了解什么我们将它命名，以便适合接收应用程序。</span><span class="sxs-lookup"><span data-stu-id="c613f-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="c613f-130">共享体验中的一台客户端将执行以下步骤来导出共享的定位点：</span><span class="sxs-lookup"><span data-stu-id="c613f-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="c613f-131">创建*WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="c613f-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="c613f-132">添加*WorldAnchors*传输</span><span class="sxs-lookup"><span data-stu-id="c613f-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="c613f-133">开始导出</span><span class="sxs-lookup"><span data-stu-id="c613f-133">Begin the export</span></span>
4. <span data-ttu-id="c613f-134">处理*OnExportDataAvailable*数据作为事件变得可用</span><span class="sxs-lookup"><span data-stu-id="c613f-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="c613f-135">处理*OnExportComplete*事件</span><span class="sxs-lookup"><span data-stu-id="c613f-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="c613f-136">我们将创建*WorldAnchorTransferBatch*封装什么我们将传输，然后将其导出到字节：</span><span class="sxs-lookup"><span data-stu-id="c613f-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="c613f-137">当数据变为可用，可用的数据段时，将字节发送到客户端或缓冲区，并通过所需的任何方式发送：</span><span class="sxs-lookup"><span data-stu-id="c613f-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="c613f-138">导出完成后，如果我们已传输数据，但序列化成功，告诉客户端要丢弃数据。</span><span class="sxs-lookup"><span data-stu-id="c613f-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="c613f-139">如果序列化成功，告诉客户端已传输的所有数据，并导入可开始：</span><span class="sxs-lookup"><span data-stu-id="c613f-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

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

### <a name="importing"></a><span data-ttu-id="c613f-140">导入</span><span class="sxs-lookup"><span data-stu-id="c613f-140">Importing</span></span>

<span data-ttu-id="c613f-141">从发送方接收的所有字节后, 我们可以导入回数据*WorldAnchorTransferBatch*并到相同物理位置锁定我们根的游戏对象。</span><span class="sxs-lookup"><span data-stu-id="c613f-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="c613f-142">注意： 导入将能够在临时有时失败，需要重试：</span><span class="sxs-lookup"><span data-stu-id="c613f-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

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

<span data-ttu-id="c613f-143">之后*GameObject*通过锁定*LockObject*调用，它将具有*WorldAnchor*这会将它保存在相同的物理位置在世界中，但它可能在在 Unity 中的其他位置的坐标空间低于其他用户。</span><span class="sxs-lookup"><span data-stu-id="c613f-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

