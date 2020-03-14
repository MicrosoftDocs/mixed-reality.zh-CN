---
title: DirectX 中的本地定位点传输
description: 说明如何通过传输空间锚点来同步两个 HoloLens 设备。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，同步，空间定位，传输，多人，查看，方案，演练，示例代码，传输，本地定位点传输，定位点导出，定位点导入
ms.openlocfilehash: f961862c3c49872484683e264fb9c62b5d0b60ee
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376024"
---
# <a name="local-anchor-transfers-in-directx"></a><span data-ttu-id="e4e54-104">DirectX 中的本地定位点传输</span><span class="sxs-lookup"><span data-stu-id="e4e54-104">Local anchor transfers in DirectX</span></span>

<span data-ttu-id="e4e54-105">在不能使用<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间锚点</a>的情况下，本地定位点传输允许一台 hololens 设备导出要由第二个 hololens 设备导入的定位点。</span><span class="sxs-lookup"><span data-stu-id="e4e54-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="e4e54-106">与<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位</a>点相比，本地定位点传输提供的功能更低，并且不支持 IOS 和 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="e4e54-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

>[!NOTE]
><span data-ttu-id="e4e54-107">本文中的代码片段当前演示了C++ C++ [ C++ ](creating-a-holographic-directx-project.md)如何使用/cx 而不是 C + 17 兼容/WinRT，这与全息项目模板中使用的不同。</span><span class="sxs-lookup"><span data-stu-id="e4e54-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="e4e54-108">概念对于C++/WinRT 项目是等效的，但你将需要转换代码。</span><span class="sxs-lookup"><span data-stu-id="e4e54-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="transferring-spatial-anchors"></a><span data-ttu-id="e4e54-109">传输空间锚</span><span class="sxs-lookup"><span data-stu-id="e4e54-109">Transferring spatial anchors</span></span>

<span data-ttu-id="e4e54-110">可以使用[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)在 Windows Mixed Reality 设备之间传输空间锚。</span><span class="sxs-lookup"><span data-stu-id="e4e54-110">You can transfer spatial anchors between Windows Mixed Reality devices by using the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="e4e54-111">利用此 API，你可以将定位点与在世界上查找确切位置所需的所有支持的传感器数据捆绑在一起，然后将该捆绑导入另一台设备。</span><span class="sxs-lookup"><span data-stu-id="e4e54-111">This API lets you bundle up an anchor with all the supporting sensor data needed to find that exact place in the world, and then import that bundle on another device.</span></span> <span data-ttu-id="e4e54-112">在第二台设备上的应用程序导入该定位点后，每个应用程序都可以使用该共享空间定位点的坐标系统呈现全息影像，然后该系统将出现在现实世界中的同一位置。</span><span class="sxs-lookup"><span data-stu-id="e4e54-112">Once the app on the second device has imported that anchor, each app can render holograms using that shared spatial anchor's coordinate system, which will then appear in the same place in the real world.</span></span>

<span data-ttu-id="e4e54-113">请注意，空间锚不能在不同的设备类型之间传输，例如，可能无法使用沉浸式耳机定位 HoloLens 空间锚。</span><span class="sxs-lookup"><span data-stu-id="e4e54-113">Note that spatial anchors are not able to transfer between different device types, for example a HoloLens spatial anchor may not be locatable using an immersive headset.</span></span>  <span data-ttu-id="e4e54-114">传输的定位点也与 iOS 或 Android 设备不兼容。</span><span class="sxs-lookup"><span data-stu-id="e4e54-114">Transferred anchors are also not compatible with iOS or Android devices.</span></span>

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="e4e54-115">设置应用程序以使用 spatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="e4e54-115">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="e4e54-116">应用必须被授予使用 spatialPerception 功能的权限，然后才能使用[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e4e54-116">Your app must be granted permission to use the spatialPerception capability before it can use the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="e4e54-117">这是必需的，因为传输空间定位点涉及到共享在该定位点附近收集的传感器映像，其中可能包括敏感信息。</span><span class="sxs-lookup"><span data-stu-id="e4e54-117">This is necessary because transferring a spatial anchor involves sharing sensor images gathered over time in vicinity of that anchor, which might include sensitive information.</span></span>

<span data-ttu-id="e4e54-118">在应用程序的 appxmanifest.xml 文件中声明此功能。</span><span class="sxs-lookup"><span data-stu-id="e4e54-118">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="e4e54-119">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="e4e54-119">Here's an example:</span></span>

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="e4e54-120">此功能来自**uap2**命名空间。</span><span class="sxs-lookup"><span data-stu-id="e4e54-120">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="e4e54-121">若要在清单中获取此命名空间的访问权限，请将其包含为 &lt;包 > 元素中的*xlmns*属性。</span><span class="sxs-lookup"><span data-stu-id="e4e54-121">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="e4e54-122">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="e4e54-122">Here's an example:</span></span>

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

<span data-ttu-id="e4e54-123">**注意：** 应用需要在运行时请求功能，然后才能访问 SpatialAnchor 导出/导入 Api。</span><span class="sxs-lookup"><span data-stu-id="e4e54-123">**NOTE:** Your app will need to request the capability at runtime before it can access SpatialAnchor export/import APIs.</span></span> <span data-ttu-id="e4e54-124">请参阅以下示例中的[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="e4e54-124">See [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in the examples below.</span></span>

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a><span data-ttu-id="e4e54-125">通过使用 SpatialAnchorTransferManager 导出定位点数据来对其进行序列化</span><span class="sxs-lookup"><span data-stu-id="e4e54-125">Serialize anchor data by exporting it with the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="e4e54-126">用于导出（序列化） [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)数据的代码示例中包含 helper 函数。</span><span class="sxs-lookup"><span data-stu-id="e4e54-126">A helper function is included in the code sample to export (serialize) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) data.</span></span> <span data-ttu-id="e4e54-127">此导出 API 序列化键值对集合中的所有定位点，这些键值对将字符串与定位点相关联。</span><span class="sxs-lookup"><span data-stu-id="e4e54-127">This export API serializes all anchors in a collection of key-value pairs associating strings with anchors.</span></span>

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

<span data-ttu-id="e4e54-128">首先，我们需要设置数据流。</span><span class="sxs-lookup"><span data-stu-id="e4e54-128">First, we need to set up the data stream.</span></span> <span data-ttu-id="e4e54-129">这将允许我们1。）使用 TryExportAnchorsAsync 将数据放置在应用拥有的缓冲区中，并使用2。从导出的字节缓冲区流中读取数据（WinRT 数据流）到自己的内存缓冲区，该缓冲区是 std：： vector&lt;字节 >。</span><span class="sxs-lookup"><span data-stu-id="e4e54-129">This will allow us to 1.) use TryExportAnchorsAsync to put the data in a buffer owned by the app, and 2.) read data from the exported byte buffer stream - which is a WinRT data stream - into our own memory buffer, which is a std::vector&lt;byte>.</span></span>

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

<span data-ttu-id="e4e54-130">我们需要请求访问空间数据的权限，包括系统导出的定位点。</span><span class="sxs-lookup"><span data-stu-id="e4e54-130">We need to ask permission to access spatial data, including anchors that are exported by the system.</span></span>

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

<span data-ttu-id="e4e54-131">如果我们确实获取了权限并导出了定位点，则可以读取数据流。</span><span class="sxs-lookup"><span data-stu-id="e4e54-131">If we do get permission and anchors are exported, we can read the data stream.</span></span> <span data-ttu-id="e4e54-132">在这里，我们还将演示如何创建用于读取数据的 DataReader 和 InputStream。</span><span class="sxs-lookup"><span data-stu-id="e4e54-132">Here, we also show how to create the DataReader and InputStream we will use to read the data.</span></span>

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

<span data-ttu-id="e4e54-133">从流中读取字节后，可以将它们保存到自己的数据缓冲区中，就像这样。</span><span class="sxs-lookup"><span data-stu-id="e4e54-133">After we read bytes from the stream, we can save them to our own data buffer like so.</span></span>

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a><span data-ttu-id="e4e54-134">使用 SpatialAnchorTransferManager 将定位点数据导入系统，从而对其进行反序列化</span><span class="sxs-lookup"><span data-stu-id="e4e54-134">Deserialize anchor data by importing it into the system using the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="e4e54-135">代码示例中包含 helper 函数以加载以前导出的数据。</span><span class="sxs-lookup"><span data-stu-id="e4e54-135">A helper function is included in the code sample to load previously exported data.</span></span> <span data-ttu-id="e4e54-136">此反序列化函数提供键值对的集合，类似于 SpatialAnchorStore 提供的内容，只不过我们从另一个源（如网络套接字）获取了此数据。</span><span class="sxs-lookup"><span data-stu-id="e4e54-136">This deserialization function provides a collection of key-value pairs, similar to what the SpatialAnchorStore provides - except that we got this data from another source, such as a network socket.</span></span> <span data-ttu-id="e4e54-137">你可以在将此数据脱机存储之前，使用应用内内存，或（如果适用）应用的 SpatialAnchorStore 来处理和原因。</span><span class="sxs-lookup"><span data-stu-id="e4e54-137">You can process and reason about this data before storing it offline, using in-app memory, or (if applicable) your app's SpatialAnchorStore.</span></span>

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

<span data-ttu-id="e4e54-138">首先，我们需要创建流对象来访问定位点数据。</span><span class="sxs-lookup"><span data-stu-id="e4e54-138">First, we need to create stream objects to access the anchor data.</span></span> <span data-ttu-id="e4e54-139">我们会将缓冲区中的数据写入系统缓冲区，因此，我们将创建一个写入内存中数据流的 DataWriter，以实现将字节缓冲区中的定位点作为 SpatialAnchors 获取到系统中的目标。</span><span class="sxs-lookup"><span data-stu-id="e4e54-139">We will be writing the data from our buffer to a system buffer, so we will create a DataWriter that writes to an in-memory data stream in order to accomplish our goal of getting anchors from a byte buffer into the system as SpatialAnchors.</span></span>

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

<span data-ttu-id="e4e54-140">同样，我们需要确保该应用有权导出空间锚数据，其中可能包括有关用户环境的隐私信息。</span><span class="sxs-lookup"><span data-stu-id="e4e54-140">Once again, we need to ensure the app has permission to export spatial anchor data, which could include private information about the user's environment.</span></span>

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

<span data-ttu-id="e4e54-141">如果允许访问，我们可以将字节从缓冲区写入系统数据流。</span><span class="sxs-lookup"><span data-stu-id="e4e54-141">If access is allowed, we can write bytes from the buffer to a system data stream.</span></span>

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

<span data-ttu-id="e4e54-142">如果我们成功地在数据流中存储字节，则可以尝试使用 SpatialAnchorTransferManager 导入该数据。</span><span class="sxs-lookup"><span data-stu-id="e4e54-142">If we were successful in storing bytes in the data stream, we can try to import that data using the SpatialAnchorTransferManager.</span></span>

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

<span data-ttu-id="e4e54-143">如果可以导入数据，我们将获得一个与定位点相关联的键值对的地图视图。</span><span class="sxs-lookup"><span data-stu-id="e4e54-143">If the data is able to be imported, we get a map view of key-value pairs associating strings with anchors.</span></span> <span data-ttu-id="e4e54-144">我们可以将其加载到自己的内存中数据集合中，并使用该集合来查找想要使用的定位点。</span><span class="sxs-lookup"><span data-stu-id="e4e54-144">We can load this into our own in-memory data collection, and use that collection to look for anchors that we are interested in using.</span></span>

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

<span data-ttu-id="e4e54-145">**注意：** 由于可以导入定位点，因此不一定意味着可以立即使用它。</span><span class="sxs-lookup"><span data-stu-id="e4e54-145">**NOTE:** Just because you can import an anchor, doesn't necessarily mean that you can use it right away.</span></span> <span data-ttu-id="e4e54-146">定位点可能位于不同的空间或其他物理位置;直到收到该定位点的设备具有与创建该定位点时所在的环境有关的可视化信息时，才会定位定位点，以还原定位点相对于已知当前环境的位置。</span><span class="sxs-lookup"><span data-stu-id="e4e54-146">The anchor might be in a different room, or another physical location entirely; the anchor won't be locatable until the device that received it has enough visual information about the environment the anchor was created in, to restore the anchor's position relative to the known current environment.</span></span> <span data-ttu-id="e4e54-147">在继续尝试将定位点用于实时内容之前，客户端实现应尝试相对于您的本地坐标系统或引用框架定位定位点。</span><span class="sxs-lookup"><span data-stu-id="e4e54-147">The client implementation should try locating the anchor relative to your local coordinate system or reference frame before continuing on to try to use it for live content.</span></span> <span data-ttu-id="e4e54-148">例如，尝试定期定位定位点，直到开始定位定位点。</span><span class="sxs-lookup"><span data-stu-id="e4e54-148">For example, try locating the anchor relative to a current coordinate system periodically until the anchor begins to be locatable.</span></span>

## <a name="special-considerations"></a><span data-ttu-id="e4e54-149">特别注意事项</span><span class="sxs-lookup"><span data-stu-id="e4e54-149">Special Considerations</span></span>

<span data-ttu-id="e4e54-150">[TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API 允许将多个[SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)导出到同一个不透明二进制 blob。</span><span class="sxs-lookup"><span data-stu-id="e4e54-150">The [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API allows multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) to be exported into the same opaque binary blob.</span></span> <span data-ttu-id="e4e54-151">不过，blob 将包含的数据有细微差别，这取决于单个 SpatialAnchor 或多个 SpatialAnchors 是否在单个调用中导出。</span><span class="sxs-lookup"><span data-stu-id="e4e54-151">However, there is a subtle difference in what data the blob will include, depending on whether a single SpatialAnchor or multiple SpatialAnchors are exported in a single call.</span></span>

### <a name="export-of-a-single-spatialanchor"></a><span data-ttu-id="e4e54-152">导出单个 SpatialAnchor</span><span class="sxs-lookup"><span data-stu-id="e4e54-152">Export of a single SpatialAnchor</span></span>

<span data-ttu-id="e4e54-153">Blob 包含 SpatialAnchor 附近环境的表示形式，以便能够在导入 SpatialAnchor 的设备上识别环境。</span><span class="sxs-lookup"><span data-stu-id="e4e54-153">The blob contains a representation of the environment in the vicinity of the SpatialAnchor so that the environment can be recognized on the device that imports the SpatialAnchor.</span></span> <span data-ttu-id="e4e54-154">导入完成后，新的 SpatialAnchor 将可供设备使用。</span><span class="sxs-lookup"><span data-stu-id="e4e54-154">After the import completes, the new SpatialAnchor will be available to the device.</span></span> <span data-ttu-id="e4e54-155">假设用户最近曾处于定位点附近，则会将其定位，并将影像附加到 SpatialAnchor。</span><span class="sxs-lookup"><span data-stu-id="e4e54-155">Assuming the user has recently been in vicinity of the anchor, it will be locatable and holograms attached to the SpatialAnchor can be rendered.</span></span> <span data-ttu-id="e4e54-156">这些全息影像将显示在导出 SpatialAnchor 的原始设备上的相同物理位置。</span><span class="sxs-lookup"><span data-stu-id="e4e54-156">These holograms will show up in the same physical location that they did on the original device which exported the SpatialAnchor.</span></span>

![导出单个 SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a><span data-ttu-id="e4e54-158">导出多个 SpatialAnchors</span><span class="sxs-lookup"><span data-stu-id="e4e54-158">Export of multiple SpatialAnchors</span></span>

<span data-ttu-id="e4e54-159">与导出单个 SpatialAnchor 一样，blob 在所有指定的 SpatialAnchors 附近都包含环境的表示形式。</span><span class="sxs-lookup"><span data-stu-id="e4e54-159">Like the export of a single SpatialAnchor, the blob contains a representation of the environment in the vicinity of all the specified SpatialAnchors.</span></span> <span data-ttu-id="e4e54-160">此外，blob 还包含有关包含的 SpatialAnchors 之间的连接的信息（如果它们位于相同的物理空间中）。</span><span class="sxs-lookup"><span data-stu-id="e4e54-160">In addition, the blob contains information about the connections between the included SpatialAnchors, if they are located in the same physical space.</span></span> <span data-ttu-id="e4e54-161">这意味着，如果导入了两个附近的 SpatialAnchors，则即使该设备只识别*第一个*SpatialAnchor 周围的环境，也会找到附加到*第二个*SpatialAnchor 的全息影像，因为这两个 SpatialAnchors 之间的计算转换所包含的数据足以用于计算 blob。</span><span class="sxs-lookup"><span data-stu-id="e4e54-161">This means that if two nearby SpatialAnchors are imported, then a hologram attached to the *second* SpatialAnchor would be locatable even if the device only recognizes the environment around the *first* SpatialAnchor, because enough data to compute transform between the two SpatialAnchors was included in the blob.</span></span> <span data-ttu-id="e4e54-162">如果这两个 SpatialAnchors 是单独导出的（两次单独调用 TryExportSpatialAnchors），则在 blob 中包含的数据可能不足以容纳第一个要定位的 SpatialAnchor。</span><span class="sxs-lookup"><span data-stu-id="e4e54-162">If the two SpatialAnchors were exported individually (two separate calls to TryExportSpatialAnchors) then there may not be enough data included in the blob for holograms attached to the second SpatialAnchor to be locatable when the first one is located.</span></span>

![使用单个 TryExportAnchorsAsync 调用导出多个定位点](images/multipleanchors.png) ![为每个定位点使用单独的 TryExportAnchorsAsync 调用导出多个定位点](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a><span data-ttu-id="e4e54-165">示例：使用 Windows：：网络：： StreamSocket 发送定位点数据</span><span class="sxs-lookup"><span data-stu-id="e4e54-165">Example: Send anchor data using a Windows::Networking::StreamSocket</span></span>

<span data-ttu-id="e4e54-166">在这里，我们提供了一个示例，说明如何通过 TCP 网络发送导出的定位点数据。</span><span class="sxs-lookup"><span data-stu-id="e4e54-166">Here, we provide an example of how to use exported anchor data by sending it across a TCP network.</span></span> <span data-ttu-id="e4e54-167">这来自 HolographicSpatialAnchorTransferSample。</span><span class="sxs-lookup"><span data-stu-id="e4e54-167">This is from the HolographicSpatialAnchorTransferSample.</span></span>

<span data-ttu-id="e4e54-168">WinRT StreamSocket 类使用 PPL 任务库。</span><span class="sxs-lookup"><span data-stu-id="e4e54-168">The WinRT StreamSocket class uses the PPL task library.</span></span> <span data-ttu-id="e4e54-169">如果出现网络错误，将使用重新引发的异常将错误返回到链中的下一个任务。</span><span class="sxs-lookup"><span data-stu-id="e4e54-169">In the case of network errors, the error is returned to the next task in the chain using an exception that is re-thrown.</span></span> <span data-ttu-id="e4e54-170">异常包含一个指示错误状态的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="e4e54-170">The exception contains an HRESULT indicating the error status.</span></span>

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a><span data-ttu-id="e4e54-171">使用带有 TCP 的 Windows：： data：： StreamSocketListener 发送导出的定位点数据</span><span class="sxs-lookup"><span data-stu-id="e4e54-171">Use a Windows::Networking::StreamSocketListener with TCP to send exported anchor data</span></span>

<span data-ttu-id="e4e54-172">创建侦听连接的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="e4e54-172">Create a server instance that listens for a connection.</span></span>

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

<span data-ttu-id="e4e54-173">接收到连接后，请使用客户端套接字连接发送定位点数据。</span><span class="sxs-lookup"><span data-stu-id="e4e54-173">When a connection is received, use the client socket connection to send anchor data.</span></span>

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

<span data-ttu-id="e4e54-174">现在，我们可以开始发送包含导出的定位点数据的数据流。</span><span class="sxs-lookup"><span data-stu-id="e4e54-174">Now, we can begin to send a data stream that contains the exported anchor data.</span></span>

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

<span data-ttu-id="e4e54-175">我们必须首先发送标头数据包，然后才能发送流本身。</span><span class="sxs-lookup"><span data-stu-id="e4e54-175">Before we can send the stream itself, we must first send a header packet.</span></span> <span data-ttu-id="e4e54-176">此标头数据包必须为固定长度，并且还必须指示作为定位点数据流的字节数组的长度。在此示例中，我们没有要发送的其他标头数据，因此我们的标头长度为4个字节，并且包含32位无符号整数。</span><span class="sxs-lookup"><span data-stu-id="e4e54-176">This header packet must be of fixed length, and it must also indicate the length of the variable array of bytes that is the anchor data stream; in the case of this example we have no other header data to send, so our header is 4 bytes long and contains a 32-bit unsigned integer.</span></span>

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

<span data-ttu-id="e4e54-177">将流长度（以字节为单位）发送到客户端后，可以继续将数据流本身写入套接字流。</span><span class="sxs-lookup"><span data-stu-id="e4e54-177">Once the stream length, in bytes, has been sent to the client, we can proceed to write the data stream itself to the socket stream.</span></span> <span data-ttu-id="e4e54-178">这将导致将定位点存储字节发送到客户端。</span><span class="sxs-lookup"><span data-stu-id="e4e54-178">This will cause the anchor store bytes to get sent to the client.</span></span>

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

<span data-ttu-id="e4e54-179">如本主题前面所述，必须准备处理包含网络错误状态消息的异常。</span><span class="sxs-lookup"><span data-stu-id="e4e54-179">As noted earlier in this topic, we must be prepared to handle exceptions containing network error status messages.</span></span> <span data-ttu-id="e4e54-180">对于不需要的错误，我们可以将异常信息写入调试控制台，如。</span><span class="sxs-lookup"><span data-stu-id="e4e54-180">For errors that are not expected, we can write the exception info to the debug console like so.</span></span> <span data-ttu-id="e4e54-181">如果我们的代码示例无法完成连接，或者无法完成发送定位点数据，就会向我们提供一个线索，告诉您发生了什么情况。</span><span class="sxs-lookup"><span data-stu-id="e4e54-181">This will give us a clue as to what happened if our code sample is unable to complete the connection, or if it is unable to finish sending the anchor data.</span></span>

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a><span data-ttu-id="e4e54-182">使用带有 TCP 的 Windows：： data：： StreamSocket 接收导出的定位点数据</span><span class="sxs-lookup"><span data-stu-id="e4e54-182">Use a Windows::Networking::StreamSocket with TCP to receive exported anchor data</span></span>

<span data-ttu-id="e4e54-183">首先，我们必须连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="e4e54-183">First, we have to connect to the server.</span></span> <span data-ttu-id="e4e54-184">此代码示例演示如何创建和配置 StreamSocket，并创建可用于通过套接字连接获取网络数据的 DataReader。</span><span class="sxs-lookup"><span data-stu-id="e4e54-184">This code sample shows how to create and configure a StreamSocket, and create a DataReader that you can use to acquire network data using the socket connection.</span></span>

<span data-ttu-id="e4e54-185">**注意：** 如果运行此示例代码，请确保在启动客户端之前配置并启动服务器。</span><span class="sxs-lookup"><span data-stu-id="e4e54-185">**NOTE:** If you run this sample code, ensure that you configure and launch the server before starting the client.</span></span>

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

<span data-ttu-id="e4e54-186">建立连接后，我们可以等待服务器发送数据。</span><span class="sxs-lookup"><span data-stu-id="e4e54-186">Once we have a connection, we can wait for the server to send data.</span></span> <span data-ttu-id="e4e54-187">为此，我们在流数据读取器上调用 LoadAsync。</span><span class="sxs-lookup"><span data-stu-id="e4e54-187">We do this by calling LoadAsync on the stream data reader.</span></span>

<span data-ttu-id="e4e54-188">我们接收到的第一组字节应始终为标头数据包，这表示定位数据流字节长度，如前一部分中所述。</span><span class="sxs-lookup"><span data-stu-id="e4e54-188">The first set of bytes we receive should always be the header packet, which indicates the anchor data stream byte length as described in the previous section.</span></span>

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

<span data-ttu-id="e4e54-189">...</span><span class="sxs-lookup"><span data-stu-id="e4e54-189">...</span></span>

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

<span data-ttu-id="e4e54-190">收到标头数据包后，我们知道应该会有多少个字节的定位数据。</span><span class="sxs-lookup"><span data-stu-id="e4e54-190">After we have received the header packet, we know how many bytes of anchor data we should expect.</span></span> <span data-ttu-id="e4e54-191">我们可以继续从流中读取这些字节。</span><span class="sxs-lookup"><span data-stu-id="e4e54-191">We can proceed to read those bytes from the stream.</span></span>

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

<span data-ttu-id="e4e54-192">下面是用于接收定位流的代码。</span><span class="sxs-lookup"><span data-stu-id="e4e54-192">Here's our code for receiving the anchor data stream.</span></span> <span data-ttu-id="e4e54-193">同样，我们将首先从流中加载字节;此操作可能需要一段时间才能完成，因为 StreamSocket 会等待接收来自网络的字节量。</span><span class="sxs-lookup"><span data-stu-id="e4e54-193">Again, we will first load the bytes from the stream; this operation may take some time to complete as the StreamSocket waits to receive that amount of bytes from the network.</span></span>

<span data-ttu-id="e4e54-194">加载操作完成后，可以读取该字节数。</span><span class="sxs-lookup"><span data-stu-id="e4e54-194">When the loading operation is complete, we can read that number of bytes.</span></span> <span data-ttu-id="e4e54-195">如果我们收到了定位流所需的字节数，可以继续导入定位数据;否则，必须有某种类型的错误。</span><span class="sxs-lookup"><span data-stu-id="e4e54-195">If we received the number of bytes that we expect for the anchor data stream, we can go ahead and import the anchor data; if not, there must have been some sort of error.</span></span> <span data-ttu-id="e4e54-196">例如，如果服务器实例在可以完成数据流发送之前终止，或者在客户端接收整个数据流之前网络出现故障，则可能会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="e4e54-196">For example, this can happen when the server instance terminates before it can finish sending the data stream, or the network goes down before the entire data stream can be received by the client.</span></span>

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

<span data-ttu-id="e4e54-197">同样，必须准备好处理未知的网络错误。</span><span class="sxs-lookup"><span data-stu-id="e4e54-197">Again, we must be prepared to handle unknown network errors.</span></span>

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

<span data-ttu-id="e4e54-198">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="e4e54-198">That's it!</span></span> <span data-ttu-id="e4e54-199">现在，您应该具有足够的信息来尝试查找通过网络接收的定位点。</span><span class="sxs-lookup"><span data-stu-id="e4e54-199">Now, you should have enough information to try locating the anchors received over the network.</span></span> <span data-ttu-id="e4e54-200">同样，请注意，客户端必须具有足够的可视化跟踪数据，空间才能成功定位定位点;如果它不能正常工作，请尝试一段时间。</span><span class="sxs-lookup"><span data-stu-id="e4e54-200">Again, note that the client must have enough visual tracking data for the space to successfully locate the anchor; if it doesn't work right away, try walking around for a while.</span></span> <span data-ttu-id="e4e54-201">如果仍不起作用，请让服务器发送更多的定位点，并使用网络通信来与适用于客户端的网络通信达成一致。</span><span class="sxs-lookup"><span data-stu-id="e4e54-201">If it still doesn't work, have the server send more anchors, and use network communications to agree on one that works for the client.</span></span> <span data-ttu-id="e4e54-202">你可以通过下载 HolographicSpatialAnchorTransferSample、配置客户端和服务器 Ip 以及将其部署到客户端和服务器 HoloLens 设备来尝试此方法。</span><span class="sxs-lookup"><span data-stu-id="e4e54-202">You can try this out by downloading the HolographicSpatialAnchorTransferSample, configuring your client and server IPs, and deploying it to client and server HoloLens devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4e54-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4e54-203">See also</span></span>
* [<span data-ttu-id="e4e54-204">并行模式库（PPL）</span><span class="sxs-lookup"><span data-stu-id="e4e54-204">Parallel Patterns Library (PPL)</span></span>](https://msdn.microsoft.com/library/dd492418.aspx)
* [<span data-ttu-id="e4e54-205">StreamSocket</span><span class="sxs-lookup"><span data-stu-id="e4e54-205">Windows.Networking.StreamSocket</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [<span data-ttu-id="e4e54-206">StreamSocketListener</span><span class="sxs-lookup"><span data-stu-id="e4e54-206">Windows.Networking.StreamSocketListener</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
