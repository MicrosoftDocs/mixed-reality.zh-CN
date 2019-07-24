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
# <a name="local-anchor-transfers-in-unity"></a>Unity 中的本地定位点传输

在不能使用<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间锚点</a>的情况下, 本地定位点传输允许一台 hololens 设备导出要由第二个 hololens 设备导入的定位点。

>[!NOTE]
>与<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位</a>点相比, 本地定位点传输提供的功能更低, 并且不支持 IOS 和 Android 设备。

### <a name="setting-the-spatialperception-capability"></a>设置 SpatialPerception 功能

为了使应用能够传输空间锚, 必须启用*SpatialPerception*功能。

如何启用*SpatialPerception*功能:
1. 在 Unity 编辑器中, 打开 **"播放机设置"** 窗格 (编辑 > Player > 项目设置)
2. 单击 **"Windows 应用商店"** 选项卡
3. 展开 **"发布设置"** , 然后在 **"功能"** 列表中检查 **"SpatialPerception"** 功能

>[!NOTE]
>如果已将 Unity 项目导出到 Visual Studio 解决方案, 则需要导出到新文件夹或[在 Visual studio 的 appxmanifest.xml 中手动设置此功能](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。

### <a name="anchor-transfer"></a>定位点传输

**命名空间：**  *UnityEngine.XR.WSA.Sharing*<br>
类型：*WorldAnchorTransferBatch*

若要传输[WorldAnchor](coordinate-systems-in-unity.md), 必须建立要传输的定位点。 一个 HoloLens 的用户将扫描其环境, 并手动或以编程方式选择空间中的一个点作为共享体验的定位点。 然后, 可以对表示此点的数据进行序列化, 并将其传输到在体验中共享的其他设备。 然后, 每个设备会反序列化定位点数据, 并尝试在空间中查找该点。 为了使定位点传输正常工作, 每个设备都必须扫描足够多的环境, 以便可以标识定位点表示的点。

### <a name="setup"></a>安装

此页上的示例代码中有几个字段需要初始化:
1. *GameObject rootGameObject*是 Unity 中的*GameObject* , 其中包含*WorldAnchor*组件。 共享体验中的一个用户会将此*GameObject* , 并将数据导出到其他用户。
2. *WorldAnchor gameRootAnchor*是位于*WorldAnchor*上的*UnityEngine。*
3. *byte [] importedData*是每个客户端通过网络接收的序列化定位点的字节数组。

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

### <a name="exporting"></a>输出

若要导出, 我们只需要一个*WorldAnchor* , 并了解我们将对其进行调用, 使接收应用有意义。 共享体验中的一个客户端将执行以下步骤以导出共享锚:
1. 创建*WorldAnchorTransferBatch*
2. 添加要传输的*WorldAnchors*
3. 开始导出
4. 在数据变为可用时处理*OnExportDataAvailable*事件
5. 处理*OnExportComplete*事件

我们会创建一个*WorldAnchorTransferBatch*来封装要传输的内容, 然后将其导出到字节:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

数据变得可用时, 将字节作为数据段发送到客户端或缓冲区, 并通过任何所需的方法发送:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

导出完成后, 如果我们已传输数据并且序列化失败, 请告知客户端丢弃数据。 如果序列化成功, 请告知客户端所有数据都已传输并可以开始导入:

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

接收到发送方发来的所有字节后, 可以将数据导入回*WorldAnchorTransferBatch* , 并将根游戏对象锁定到相同的物理位置。 注意: 有时 transiently 会失败, 需要重试:

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

通过*LockObject*调用锁定*GameObject*后, 它将具有一个*WorldAnchor* , 它会将其保持在世界上相同的物理位置, 但它可能与其他用户在 Unity 坐标空间中的位置不同。

