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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593059"
---
# <a name="local-anchor-transfers-in-unity"></a>在 Unity 中的本地定位点传输

在不能使用情况下<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a>，本地的定位点传输启用一个 HoloLens 设备导出要导入第二个 HoloLens 设备的定位点。

>[!NOTE]
>本地的定位点复制提供了比更不稳定的定位点召回<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a>，以及 iOS 和 Android 设备不支持这种方法。

### <a name="setting-the-spatialperception-capability"></a>设置 SpatialPerception 功能

为了使应用程序传输空间定位点*SpatialPerception*必须启用功能。

如何启用*SpatialPerception*功能：
1. 在 Unity 编辑器中打开 **"播放器设置"** 窗格 (编辑 > 项目设置 > 播放机)
2. 单击 **"Windows 应用商店"** 选项卡
3. 展开 **"发布设置"** ，并检查 **"SpatialPerception"** 中的功能 **"功能"** 列表

>[!NOTE]
>如果你已向 Visual Studio 解决方案导出你的 Unity 项目，你将需要导出到新文件夹或手动[在 Visual Studio 中的 AppxManifest 中设置此功能](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。

### <a name="anchor-transfer"></a>定位点传输

**命名空间：***UnityEngine.XR.WSA.Sharing*<br>
类型：*WorldAnchorTransferBatch*

要传输[WorldAnchor](coordinate-systems-in-unity.md)，其中一个必须建立要传输的定位点。 一个 HoloLens 用户扫描其环境，并手动或以编程方式为共享体验的定位点的空间中选择一个点。 然后，将表示此点的数据序列化并将其传输到体验中共享的其他设备。 每个设备然后反序列化的定位点数据，并尝试在空间中找到该点。 为了使定位点传输工作，必须具有每个设备扫描中足够多的环境，以便可以标识定位标记所表示的点。

### <a name="setup"></a>安装

此页上的示例代码具有几个字段，将需要进行初始化：
1. *GameObject rootGameObject*是*GameObject*在 Unity 中具有*WorldAnchor*组件在其上。 中的共享体验的一个用户会将这*GameObject*和将数据导出到其他用户。
2. *WorldAnchor gameRootAnchor*是*UnityEngine.XR.WSA.WorldAnchor*这也是*rootGameObject*。
3. *字节 [] importedData*是序列化的定位点在网络上接收每个客户端的字节数组。

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

### <a name="exporting"></a>导出

若要导出，我们只需*WorldAnchor*并了解什么我们将它命名，以便适合接收应用程序。 共享体验中的一台客户端将执行以下步骤来导出共享的定位点：
1. 创建*WorldAnchorTransferBatch*
2. 添加*WorldAnchors*传输
3. 开始导出
4. 处理*OnExportDataAvailable*数据作为事件变得可用
5. 处理*OnExportComplete*事件

我们将创建*WorldAnchorTransferBatch*封装什么我们将传输，然后将其导出到字节：

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

当数据变为可用，可用的数据段时，将字节发送到客户端或缓冲区，并通过所需的任何方式发送：

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

导出完成后，如果我们已传输数据，但序列化成功，告诉客户端要丢弃数据。 如果序列化成功，告诉客户端已传输的所有数据，并导入可开始：

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

### <a name="importing"></a>导入

从发送方接收的所有字节后, 我们可以导入回数据*WorldAnchorTransferBatch*并到相同物理位置锁定我们根的游戏对象。 注意： 导入将能够在临时有时失败，需要重试：

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

之后*GameObject*通过锁定*LockObject*调用，它将具有*WorldAnchor*这会将它保存在相同的物理位置在世界中，但它可能在在 Unity 中的其他位置的坐标空间低于其他用户。

