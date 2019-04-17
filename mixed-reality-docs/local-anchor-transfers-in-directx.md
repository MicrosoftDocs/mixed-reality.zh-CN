---
title: 在 DirectX 本地定位点传输
description: 介绍如何同步两个 HoloLens 设备将传输空间的定位点。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，同步，空间定位点、 传输、 之多人游戏，查看方案、 演练、 示例代码、 传输、 本地定位点传输、 定位点导出、 定位点导入
ms.openlocfilehash: 5d03f4bfa764b9948ec4718bce86127cfcc3e303
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593061"
---
# <a name="local-anchor-transfers-in-directx"></a><span data-ttu-id="c6927-104">在 DirectX 本地定位点传输</span><span class="sxs-lookup"><span data-stu-id="c6927-104">Local anchor transfers in DirectX</span></span>

<span data-ttu-id="c6927-105">在不能使用情况下<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a>，本地的定位点传输启用一个 HoloLens 设备导出要导入第二个 HoloLens 设备的定位点。</span><span class="sxs-lookup"><span data-stu-id="c6927-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="c6927-106">本地的定位点复制提供了比更不稳定的定位点召回<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a>，以及 iOS 和 Android 设备不支持这种方法。</span><span class="sxs-lookup"><span data-stu-id="c6927-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

>[!NOTE]
><span data-ttu-id="c6927-107">这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="c6927-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="c6927-108">这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。</span><span class="sxs-lookup"><span data-stu-id="c6927-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="transferring-spatial-anchors"></a><span data-ttu-id="c6927-109">传输空间的定位点</span><span class="sxs-lookup"><span data-stu-id="c6927-109">Transferring spatial anchors</span></span>

<span data-ttu-id="c6927-110">可以使用 Windows Mixed Reality 设备之间传输空间的定位点[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c6927-110">You can transfer spatial anchors between Windows Mixed Reality devices by using the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="c6927-111">此 API 允许您所有支持传感器所需的数据在领域中，查找该确切位置捆绑定位点，然后导入另一台设备上的该软件包。</span><span class="sxs-lookup"><span data-stu-id="c6927-111">This API lets you bundle up an anchor with all the supporting sensor data needed to find that exact place in the world, and then import that bundle on another device.</span></span> <span data-ttu-id="c6927-112">第二个设备上的应用已导入后的定位点，每个应用可以呈现全息使用共享空间定位点的坐标系统，随后会显示在现实生活中的同一位置。</span><span class="sxs-lookup"><span data-stu-id="c6927-112">Once the app on the second device has imported that anchor, each app can render holograms using that shared spatial anchor's coordinate system, which will then appear in the same place in the real world.</span></span>

<span data-ttu-id="c6927-113">请注意，空间的定位点不能将不同类型的设备之间传输，例如 HoloLens 空间定位点可能无法使用沉浸式头戴式可定位。</span><span class="sxs-lookup"><span data-stu-id="c6927-113">Note that spatial anchors are not able to transfer between different device types, for example a HoloLens spatial anchor may not be locatable using an immersive headset.</span></span>  <span data-ttu-id="c6927-114">传输的定位点也不是与 iOS 或 Android 设备兼容。</span><span class="sxs-lookup"><span data-stu-id="c6927-114">Transferred anchors are also not compatible with iOS or Android devices.</span></span>

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="c6927-115">将您的应用程序设置为使用 spatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="c6927-115">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="c6927-116">您的应用程序必须授予使用 spatialPerception 功能，然后才能使用权限[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c6927-116">Your app must be granted permission to use the spatialPerception capability before it can use the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="c6927-117">这是必需的因为传输空间定位点涉及到共享中的该定位点，这可能包括敏感信息的邻近范围随着时间的推移收集的传感器映像。</span><span class="sxs-lookup"><span data-stu-id="c6927-117">This is necessary because transferring a spatial anchor involves sharing sensor images gathered over time in vicinity of that anchor, which might include sensitive information.</span></span>

<span data-ttu-id="c6927-118">声明此功能在您的应用程序的 package.appxmanifest 文件中。</span><span class="sxs-lookup"><span data-stu-id="c6927-118">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="c6927-119">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="c6927-119">Here's an example:</span></span>

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="c6927-120">功能是来自**uap2**命名空间。</span><span class="sxs-lookup"><span data-stu-id="c6927-120">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="c6927-121">若要访问此命名空间在清单中，将其作为包含*xlmns*属性中&lt;包 > 元素。</span><span class="sxs-lookup"><span data-stu-id="c6927-121">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="c6927-122">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="c6927-122">Here's an example:</span></span>

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

<span data-ttu-id="c6927-123">**注意：** 您的应用程序将需要它才能访问 SpatialAnchor 导出/导入 Api 请求在运行时的功能。</span><span class="sxs-lookup"><span data-stu-id="c6927-123">**NOTE:** Your app will need to request the capability at runtime before it can access SpatialAnchor export/import APIs.</span></span> <span data-ttu-id="c6927-124">请参阅[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx)下面的示例。</span><span class="sxs-lookup"><span data-stu-id="c6927-124">See [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in the examples below.</span></span>

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a><span data-ttu-id="c6927-125">通过导出 SpatialAnchorTransferManager 与定位点数据进行序列化</span><span class="sxs-lookup"><span data-stu-id="c6927-125">Serialize anchor data by exporting it with the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="c6927-126">若要导出的代码示例中包含的帮助器函数 （序列化） [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)数据。</span><span class="sxs-lookup"><span data-stu-id="c6927-126">A helper function is included in the code sample to export (serialize) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) data.</span></span> <span data-ttu-id="c6927-127">此导出 API 序列化将字符串与定位点相关联的键 / 值对的集合中的所有定位点。</span><span class="sxs-lookup"><span data-stu-id="c6927-127">This export API serializes all anchors in a collection of key-value pairs associating strings with anchors.</span></span>

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

<span data-ttu-id="c6927-128">首先，我们需要设置的数据流。</span><span class="sxs-lookup"><span data-stu-id="c6927-128">First, we need to set up the data stream.</span></span> <span data-ttu-id="c6927-129">这样，我们为 1。）使用 TryExportAnchorsAsync 来将数据放在缓冲区中拥有的应用程序中和 2。）从-这是 WinRT 数据流-导出的字节缓冲区流中读取数据，到我们自己的内存缓冲区中，这是 std:: vector&lt;字节 >。</span><span class="sxs-lookup"><span data-stu-id="c6927-129">This will allow us to 1.) use TryExportAnchorsAsync to put the data in a buffer owned by the app, and 2.) read data from the exported byte buffer stream - which is a WinRT data stream - into our own memory buffer, which is a std::vector&lt;byte>.</span></span>

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

<span data-ttu-id="c6927-130">我们需要请求访问空间数据，包括导出的系统的定位点的权限。</span><span class="sxs-lookup"><span data-stu-id="c6927-130">We need to ask permission to access spatial data, including anchors that are exported by the system.</span></span>

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

<span data-ttu-id="c6927-131">如果我们执行获取权限，而导出的定位点，我们可以读取该数据流。</span><span class="sxs-lookup"><span data-stu-id="c6927-131">If we do get permission and anchors are exported, we can read the data stream.</span></span> <span data-ttu-id="c6927-132">在这里，我们还展示如何创建 DataReader 和 InputStream 我们将使用要读取的数据。</span><span class="sxs-lookup"><span data-stu-id="c6927-132">Here, we also show how to create the DataReader and InputStream we will use to read the data.</span></span>

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

<span data-ttu-id="c6927-133">我们从流中读取字节后，我们可以将其保存到我们自己的数据缓冲区如下所示。</span><span class="sxs-lookup"><span data-stu-id="c6927-133">After we read bytes from the stream, we can save them to our own data buffer like so.</span></span>

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a><span data-ttu-id="c6927-134">导入系统使用 SpatialAnchorTransferManager 定位点数据反序列化</span><span class="sxs-lookup"><span data-stu-id="c6927-134">Deserialize anchor data by importing it into the system using the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="c6927-135">加载以前导出的数据的代码示例中包含的帮助器函数。</span><span class="sxs-lookup"><span data-stu-id="c6927-135">A helper function is included in the code sample to load previously exported data.</span></span> <span data-ttu-id="c6927-136">此反序列化函数提供了一系列键-值对，类似于 SpatialAnchorStore 提供什么-，不同之处在于我们从其他源，例如网络套接字此数据。</span><span class="sxs-lookup"><span data-stu-id="c6927-136">This deserialization function provides a collection of key-value pairs, similar to what the SpatialAnchorStore provides - except that we got this data from another source, such as a network socket.</span></span> <span data-ttu-id="c6927-137">可以处理和有关此数据之前将其存储脱机，并使用应用程序内内存的原因 （如果适用） 或应用程序的 SpatialAnchorStore。</span><span class="sxs-lookup"><span data-stu-id="c6927-137">You can process and reason about this data before storing it offline, using in-app memory, or (if applicable) your app's SpatialAnchorStore.</span></span>

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

<span data-ttu-id="c6927-138">首先，我们需要创建要访问的定位点数据的流对象。</span><span class="sxs-lookup"><span data-stu-id="c6927-138">First, we need to create stream objects to access the anchor data.</span></span> <span data-ttu-id="c6927-139">我们将把数据写入从我们的缓冲区系统缓冲区，因此我们将创建为我们的目标为 SpatialAnchors 系统从字节缓冲区中获取的定位点的写入内存中数据流 DataWriter。</span><span class="sxs-lookup"><span data-stu-id="c6927-139">We will be writing the data from our buffer to a system buffer, so we will create a DataWriter that writes to an in-memory data stream in order to accomplish our goal of getting anchors from a byte buffer into the system as SpatialAnchors.</span></span>

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

<span data-ttu-id="c6927-140">再次重申，我们需要确保应用程序具有权限才能导出空间定位点的数据，它可能包含有关用户的环境的私人信息。</span><span class="sxs-lookup"><span data-stu-id="c6927-140">Once again, we need to ensure the app has permission to export spatial anchor data, which could include private information about the user's environment.</span></span>

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

<span data-ttu-id="c6927-141">如果允许访问，我们可以从缓冲区到系统的数据流中写入字节。</span><span class="sxs-lookup"><span data-stu-id="c6927-141">If access is allowed, we can write bytes from the buffer to a system data stream.</span></span>

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

<span data-ttu-id="c6927-142">如果我们已成功存储该数据流中的字节数，我们可以尝试使用 SpatialAnchorTransferManager 这些数据导入。</span><span class="sxs-lookup"><span data-stu-id="c6927-142">If we were successful in storing bytes in the data stream, we can try to import that data using the SpatialAnchorTransferManager.</span></span>

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

<span data-ttu-id="c6927-143">如果能导入数据，我们获取键 / 值对将字符串与定位点相关联的地图视图。</span><span class="sxs-lookup"><span data-stu-id="c6927-143">If the data is able to be imported, we get a map view of key-value pairs associating strings with anchors.</span></span> <span data-ttu-id="c6927-144">我们可以将此加载到我们自己的内存中数据的集合，并使用该集合查找，我们感兴趣使用的定位点。</span><span class="sxs-lookup"><span data-stu-id="c6927-144">We can load this into our own in-memory data collection, and use that collection to look for anchors that we are interested in using.</span></span>

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

<span data-ttu-id="c6927-145">**注意：** 您可以导入定位点，并不一定意味着可以立即使用。</span><span class="sxs-lookup"><span data-stu-id="c6927-145">**NOTE:** Just because you can import an anchor, doesn't necessarily mean that you can use it right away.</span></span> <span data-ttu-id="c6927-146">定位点可能是在另一个房间或另一个物理位置中完全;定位点不会是可定位，直到接收到它的设备具有足够 visual 定位点创建在中，若要还原的定位点位置相对于已知的当前环境的环境信息。</span><span class="sxs-lookup"><span data-stu-id="c6927-146">The anchor might be in a different room, or another physical location entirely; the anchor won't be locatable until the device that received it has enough visual information about the environment the anchor was created in, to restore the anchor's position relative to the known current environment.</span></span> <span data-ttu-id="c6927-147">客户端实现应尝试上继续尝试使用它的实时内容之前查找相对于本地坐标系统或参考框架的定位点。</span><span class="sxs-lookup"><span data-stu-id="c6927-147">The client implementation should try locating the anchor relative to your local coordinate system or reference frame before continuing on to try to use it for live content.</span></span> <span data-ttu-id="c6927-148">例如，尝试查找相对于当前的坐标系统的定位点定期直到定位点开始会找到该项。</span><span class="sxs-lookup"><span data-stu-id="c6927-148">For example, try locating the anchor relative to a current coordinate system periodically until the anchor begins to be locatable.</span></span>

## <a name="special-considerations"></a><span data-ttu-id="c6927-149">特别注意的事项</span><span class="sxs-lookup"><span data-stu-id="c6927-149">Special Considerations</span></span>

<span data-ttu-id="c6927-150">[TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API 允许多个[SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)要导出到同一个不透明二进制 blob。</span><span class="sxs-lookup"><span data-stu-id="c6927-150">The [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API allows multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) to be exported into the same opaque binary blob.</span></span> <span data-ttu-id="c6927-151">但是，是包含 blob，具体取决于是否在单个调用中导出单个 SpatialAnchor 或多个 SpatialAnchors 哪些数据的细微差别。</span><span class="sxs-lookup"><span data-stu-id="c6927-151">However, there is a subtle difference in what data the blob will include, depending on whether a single SpatialAnchor or multiple SpatialAnchors are exported in a single call.</span></span>

### <a name="export-of-a-single-spatialanchor"></a><span data-ttu-id="c6927-152">单个 SpatialAnchor 的导出</span><span class="sxs-lookup"><span data-stu-id="c6927-152">Export of a single SpatialAnchor</span></span>

<span data-ttu-id="c6927-153">Blob 包含在附近出现 SpatialAnchor 环境的表示形式，因此环境可以识别导入 SpatialAnchor 在设备上。</span><span class="sxs-lookup"><span data-stu-id="c6927-153">The blob contains a representation of the environment in the vicinity of the SpatialAnchor so that the environment can be recognized on the device that imports the SpatialAnchor.</span></span> <span data-ttu-id="c6927-154">导入完成后，新 SpatialAnchor 将对设备可用。</span><span class="sxs-lookup"><span data-stu-id="c6927-154">After the import completes, the new SpatialAnchor will be available to the device.</span></span> <span data-ttu-id="c6927-155">假设用户最近已在邻近的定位点，它将是可定位和全息附加到 SpatialAnchor 可以呈现。</span><span class="sxs-lookup"><span data-stu-id="c6927-155">Assuming the user has recently been in vicinity of the anchor, it will be locatable and holograms attached to the SpatialAnchor can be rendered.</span></span> <span data-ttu-id="c6927-156">这些全息将显示在它们未导出 SpatialAnchor 在原始设备的相同物理位置。</span><span class="sxs-lookup"><span data-stu-id="c6927-156">These holograms will show up in the same physical location that they did on the original device which exported the SpatialAnchor.</span></span>

![单个 SpatialAnchor 的导出](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a><span data-ttu-id="c6927-158">多个 SpatialAnchors 导出</span><span class="sxs-lookup"><span data-stu-id="c6927-158">Export of multiple SpatialAnchors</span></span>

<span data-ttu-id="c6927-159">单个 SpatialAnchor 的导出，如 blob 包含在所有指定 SpatialAnchors 附近出现环境的表示形式。</span><span class="sxs-lookup"><span data-stu-id="c6927-159">Like the export of a single SpatialAnchor, the blob contains a representation of the environment in the vicinity of all the specified SpatialAnchors.</span></span> <span data-ttu-id="c6927-160">此外，该 blob 包含之间包含 SpatialAnchors，连接信息，如果它们位于同一物理空间中。</span><span class="sxs-lookup"><span data-stu-id="c6927-160">In addition, the blob contains information about the connections between the included SpatialAnchors, if they are located in the same physical space.</span></span> <span data-ttu-id="c6927-161">这意味着，如果两个邻近 SpatialAnchors 导入，然后一张全息图附加到*第二个*SpatialAnchor 将是可定位，即使该设备仅识别的环境*第一个*SpatialAnchor，因为数据不足，无法计算两个 SpatialAnchors 之间进行转换中包含该 blob。</span><span class="sxs-lookup"><span data-stu-id="c6927-161">This means that if two nearby SpatialAnchors are imported, then a hologram attached to the *second* SpatialAnchor would be locatable even if the device only recognizes the environment around the *first* SpatialAnchor, because enough data to compute transform between the two SpatialAnchors was included in the blob.</span></span> <span data-ttu-id="c6927-162">如果两个 SpatialAnchors 单独导出 （两个单独的调用 TryExportSpatialAnchors） 则可能不会有足够全息附加到第二个 SpatialAnchor 为可定位第一个 blob 中包含的数据的位置。</span><span class="sxs-lookup"><span data-stu-id="c6927-162">If the two SpatialAnchors were exported individually (two separate calls to TryExportSpatialAnchors) then there may not be enough data included in the blob for holograms attached to the second SpatialAnchor to be locatable when the first one is located.</span></span>

![使用单个 TryExportAnchorsAsync 调用导出的多个定位点](images/multipleanchors.png) ![导出的每个定位点使用单独的 TryExportAnchorsAsync 调用多个定位点](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a><span data-ttu-id="c6927-165">例如：发送使用 Windows::Networking::StreamSocket 的定位点数据</span><span class="sxs-lookup"><span data-stu-id="c6927-165">Example: Send anchor data using a Windows::Networking::StreamSocket</span></span>

<span data-ttu-id="c6927-166">此处，我们介绍如何通过将其发送 TCP 网络上使用导出的定位点数据的示例。</span><span class="sxs-lookup"><span data-stu-id="c6927-166">Here, we provide an example of how to use exported anchor data by sending it across a TCP network.</span></span> <span data-ttu-id="c6927-167">这是从 HolographicSpatialAnchorTransferSample。</span><span class="sxs-lookup"><span data-stu-id="c6927-167">This is from the HolographicSpatialAnchorTransferSample.</span></span>

<span data-ttu-id="c6927-168">WinRT StreamSocket 类使用 PPL 任务库。</span><span class="sxs-lookup"><span data-stu-id="c6927-168">The WinRT StreamSocket class uses the PPL task library.</span></span> <span data-ttu-id="c6927-169">如果网络发生错误，使用重新引发的异常链中下一项任务返回的错误。</span><span class="sxs-lookup"><span data-stu-id="c6927-169">In the case of network errors, the error is returned to the next task in the chain using an exception that is re-thrown.</span></span> <span data-ttu-id="c6927-170">该异常包含一个 HRESULT，指示错误状态。</span><span class="sxs-lookup"><span data-stu-id="c6927-170">The exception contains an HRESULT indicating the error status.</span></span>

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a><span data-ttu-id="c6927-171">使用 TCP 和 Windows::Networking::StreamSocketListener 发送导出的定位点数据</span><span class="sxs-lookup"><span data-stu-id="c6927-171">Use a Windows::Networking::StreamSocketListener with TCP to send exported anchor data</span></span>

<span data-ttu-id="c6927-172">创建侦听连接的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="c6927-172">Create a server instance that listens for a connection.</span></span>

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

<span data-ttu-id="c6927-173">收到连接后，使用客户端套接字连接发送定位点数据。</span><span class="sxs-lookup"><span data-stu-id="c6927-173">When a connection is received, use the client socket connection to send anchor data.</span></span>

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

<span data-ttu-id="c6927-174">现在，我们可以开始发送包含导出的定位点数据的数据流。</span><span class="sxs-lookup"><span data-stu-id="c6927-174">Now, we can begin to send a data stream that contains the exported anchor data.</span></span>

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

<span data-ttu-id="c6927-175">我们可以将流本身发送之前，我们首先必须将标头数据包发送。</span><span class="sxs-lookup"><span data-stu-id="c6927-175">Before we can send the stream itself, we must first send a header packet.</span></span> <span data-ttu-id="c6927-176">此标头数据包必须是固定长度，并且它还必须指示的字节是定位点数据流; 变量的数组的长度在此示例中我们有其他要发送的标头数据，因此我们标头是 4 个字节长，包含 32 位无符号的整数。</span><span class="sxs-lookup"><span data-stu-id="c6927-176">This header packet must be of fixed length, and it must also indicate the length of the variable array of bytes that is the anchor data stream; in the case of this example we have no other header data to send, so our header is 4 bytes long and contains a 32-bit unsigned integer.</span></span>

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

<span data-ttu-id="c6927-177">之后流长度，以字节为单位，已发送到客户端，我们可以继续进行到套接字流写入数据流本身。</span><span class="sxs-lookup"><span data-stu-id="c6927-177">Once the stream length, in bytes, has been sent to the client, we can proceed to write the data stream itself to the socket stream.</span></span> <span data-ttu-id="c6927-178">这会导致要发送到客户端的定位点存储字节。</span><span class="sxs-lookup"><span data-stu-id="c6927-178">This will cause the anchor store bytes to get sent to the client.</span></span>

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

<span data-ttu-id="c6927-179">如本主题中前面所述，我们必须准备好处理包含网络错误状态消息的异常。</span><span class="sxs-lookup"><span data-stu-id="c6927-179">As noted earlier in this topic, we must be prepared to handle exceptions containing network error status messages.</span></span> <span data-ttu-id="c6927-180">对于没有按预期的错误，我们可以将异常信息写入到调试控制台如下所示。</span><span class="sxs-lookup"><span data-stu-id="c6927-180">For errors that are not expected, we can write the exception info to the debug console like so.</span></span> <span data-ttu-id="c6927-181">这将向我们提供有关我们的代码示例是无法完成连接，或无法完成发送的定位点数据是否发生了什么情况的线索。</span><span class="sxs-lookup"><span data-stu-id="c6927-181">This will give us a clue as to what happened if our code sample is unable to complete the connection, or if it is unable to finish sending the anchor data.</span></span>

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a><span data-ttu-id="c6927-182">使用与 TCP Windows::Networking::StreamSocket 接收导出的定位点数据</span><span class="sxs-lookup"><span data-stu-id="c6927-182">Use a Windows::Networking::StreamSocket with TCP to receive exported anchor data</span></span>

<span data-ttu-id="c6927-183">首先，我们必须连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="c6927-183">First, we have to connect to the server.</span></span> <span data-ttu-id="c6927-184">此代码示例演示如何创建和配置 StreamSocket，以及创建可用于获取网络数据使用套接字连接 DataReader。</span><span class="sxs-lookup"><span data-stu-id="c6927-184">This code sample shows how to create and configure a StreamSocket, and create a DataReader that you can use to acquire network data using the socket connection.</span></span>

<span data-ttu-id="c6927-185">**注意：** 如果运行此示例代码，请确保配置和启动客户端之前启动服务器。</span><span class="sxs-lookup"><span data-stu-id="c6927-185">**NOTE:** If you run this sample code, ensure that you configure and launch the server before starting the client.</span></span>

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

<span data-ttu-id="c6927-186">一旦我们有一个连接，我们可以等待服务器以发送数据。</span><span class="sxs-lookup"><span data-stu-id="c6927-186">Once we have a connection, we can wait for the server to send data.</span></span> <span data-ttu-id="c6927-187">我们通过调用 LoadAsync 流数据读取器执行此操作。</span><span class="sxs-lookup"><span data-stu-id="c6927-187">We do this by calling LoadAsync on the stream data reader.</span></span>

<span data-ttu-id="c6927-188">我们收到的字节数的第一组应始终为标头数据包，指示定位点数据流字节长度，在上一部分中所述。</span><span class="sxs-lookup"><span data-stu-id="c6927-188">The first set of bytes we receive should always be the header packet, which indicates the anchor data stream byte length as described in the previous section.</span></span>

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

<span data-ttu-id="c6927-189">...</span><span class="sxs-lookup"><span data-stu-id="c6927-189">...</span></span>

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

<span data-ttu-id="c6927-190">我们已收到的标头数据包后，我们知道我们应期望的定位点数据的字节数。</span><span class="sxs-lookup"><span data-stu-id="c6927-190">After we have received the header packet, we know how many bytes of anchor data we should expect.</span></span> <span data-ttu-id="c6927-191">我们可以继续进行从流中读取这些字节。</span><span class="sxs-lookup"><span data-stu-id="c6927-191">We can proceed to read those bytes from the stream.</span></span>

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

<span data-ttu-id="c6927-192">下面是我们的代码用于接收定位点的数据流。</span><span class="sxs-lookup"><span data-stu-id="c6927-192">Here's our code for receiving the anchor data stream.</span></span> <span data-ttu-id="c6927-193">同样，我们将首先加载字节从流;此操作可能需要一些时间才能完成，因为 StreamSocket 等待从网络接收的字节的数量。</span><span class="sxs-lookup"><span data-stu-id="c6927-193">Again, we will first load the bytes from the stream; this operation may take some time to complete as the StreamSocket waits to receive that amount of bytes from the network.</span></span>

<span data-ttu-id="c6927-194">加载操作完成后，我们可以读取字节的数。</span><span class="sxs-lookup"><span data-stu-id="c6927-194">When the loading operation is complete, we can read that number of bytes.</span></span> <span data-ttu-id="c6927-195">如果我们未收到我们希望为定位点数据的流的字节数，我们可以继续并导入的定位点数据;如果没有，则必须已被某种形式的错误。</span><span class="sxs-lookup"><span data-stu-id="c6927-195">If we received the number of bytes that we expect for the anchor data stream, we can go ahead and import the anchor data; if not, there must have been some sort of error.</span></span> <span data-ttu-id="c6927-196">例如，这可能发生的服务器实例终止之前它可以完成发送数据流，或可由客户端接收整个数据流之前，在网络出现故障时。</span><span class="sxs-lookup"><span data-stu-id="c6927-196">For example, this can happen when the server instance terminates before it can finish sending the data stream, or the network goes down before the entire data stream can be received by the client.</span></span>

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

<span data-ttu-id="c6927-197">同样，我们必须准备好处理未知的网络错误。</span><span class="sxs-lookup"><span data-stu-id="c6927-197">Again, we must be prepared to handle unknown network errors.</span></span>

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

<span data-ttu-id="c6927-198">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="c6927-198">That's it!</span></span> <span data-ttu-id="c6927-199">现在，应该有足够的信息来尝试查找通过网络接收的定位点。</span><span class="sxs-lookup"><span data-stu-id="c6927-199">Now, you should have enough information to try locating the anchors received over the network.</span></span> <span data-ttu-id="c6927-200">同样，请注意，客户端必须具有足够空间来成功地定位到定位点; 的直观跟踪数据如果它不会立即运行，请尝试移动办公了一段时间。</span><span class="sxs-lookup"><span data-stu-id="c6927-200">Again, note that the client must have enough visual tracking data for the space to successfully locate the anchor; if it doesn't work right away, try walking around for a while.</span></span> <span data-ttu-id="c6927-201">如果它仍不起作用，必须将发送多个定位点，并使用网络通信同意一个适用于客户端上的服务器。</span><span class="sxs-lookup"><span data-stu-id="c6927-201">If it still doesn't work, have the server send more anchors, and use network communications to agree on one that works for the client.</span></span> <span data-ttu-id="c6927-202">您可以试用此下载 HolographicSpatialAnchorTransferSample、 配置客户端和服务器 Ip，以及将其部署到客户端和服务器 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="c6927-202">You can try this out by downloading the HolographicSpatialAnchorTransferSample, configuring your client and server IPs, and deploying it to client and server HoloLens devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6927-203">请参阅</span><span class="sxs-lookup"><span data-stu-id="c6927-203">See also</span></span>
* [<span data-ttu-id="c6927-204">并行模式库 (PPL)</span><span class="sxs-lookup"><span data-stu-id="c6927-204">Parallel Patterns Library (PPL)</span></span>](https://msdn.microsoft.com/library/dd492418.aspx)
* [<span data-ttu-id="c6927-205">Windows.Networking.StreamSocket</span><span class="sxs-lookup"><span data-stu-id="c6927-205">Windows.Networking.StreamSocket</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [<span data-ttu-id="c6927-206">Windows.Networking.StreamSocketListener</span><span class="sxs-lookup"><span data-stu-id="c6927-206">Windows.Networking.StreamSocketListener</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
