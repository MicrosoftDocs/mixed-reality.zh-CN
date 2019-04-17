---
title: 跟踪的 QR 代码
description: 了解如何启用跟踪您的 Windows Mixed Reality 沉浸式 (VR) 头戴式 QR 码和 VR 应用程序中实现的功能。
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr lbe，基于位置娱乐、 vr 拱廊沉浸式拱廊，qr，qr 代码
ms.openlocfilehash: b0f4480496c15f811979f76143acbd456d89e249
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593071"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="4997b-104">跟踪的 QR 代码</span><span class="sxs-lookup"><span data-stu-id="4997b-104">QR code tracking</span></span>

<span data-ttu-id="4997b-105">在沉浸式 (VR) 耳机 Windows Mixed Reality 驱动程序中实现跟踪的 QR 代码。</span><span class="sxs-lookup"><span data-stu-id="4997b-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="4997b-106">通过启用耳机驱动程序中的 QR 代码跟踪器，耳机扫描 QR 码和它们报告给希望应用程序。</span><span class="sxs-lookup"><span data-stu-id="4997b-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="4997b-107">此功能才可用的[Windows 10 2018 年 10 月更新 (也称为 RS5)](release-notes-october-2018.md)。</span><span class="sxs-lookup"><span data-stu-id="4997b-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="4997b-108">这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="4997b-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="4997b-109">这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。</span><span class="sxs-lookup"><span data-stu-id="4997b-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="4997b-110">设备支持</span><span class="sxs-lookup"><span data-stu-id="4997b-110">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4997b-111">功能</span><span class="sxs-lookup"><span data-stu-id="4997b-111">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="4997b-112"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="4997b-112"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="4997b-113"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="4997b-113"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4997b-114">跟踪的 QR 代码</span><span class="sxs-lookup"><span data-stu-id="4997b-114">QR code tracking</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="4997b-115">✔️</span><span class="sxs-lookup"><span data-stu-id="4997b-115">✔️</span></span></td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="4997b-116">启用和禁用 QR 代码跟踪您的头戴式</span><span class="sxs-lookup"><span data-stu-id="4997b-116">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="4997b-117">注意：本部分中时才有效[Windows 10 2018 年 10 月更新 (也称为 RS5)](release-notes-october-2018.md)。</span><span class="sxs-lookup"><span data-stu-id="4997b-117">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="4997b-118">从 19 h 1 及更高版本生成不需要执行此操作。</span><span class="sxs-lookup"><span data-stu-id="4997b-118">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="4997b-119">是否正在开发一个混合的现实应用，它将利用 QR 代码跟踪，或者你是其中一个应用的客户，你将需要手动开启跟踪耳机的驱动程序中的 QR 代码。</span><span class="sxs-lookup"><span data-stu-id="4997b-119">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="4997b-120">为了**开启 QR 代码跟踪**的沉浸式的 (VR) 耳机：</span><span class="sxs-lookup"><span data-stu-id="4997b-120">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="4997b-121">关闭您的 PC 上的混合的现实门户应用。</span><span class="sxs-lookup"><span data-stu-id="4997b-121">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="4997b-122">从您的 PC 耳机中拔出。</span><span class="sxs-lookup"><span data-stu-id="4997b-122">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="4997b-123">在命令提示符处运行以下脚本：</span><span class="sxs-lookup"><span data-stu-id="4997b-123">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="4997b-124">重新连接到您的 PC 将耳机。</span><span class="sxs-lookup"><span data-stu-id="4997b-124">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="4997b-125">为了**关闭跟踪的 QR 码**的沉浸式的 (VR) 耳机：</span><span class="sxs-lookup"><span data-stu-id="4997b-125">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="4997b-126">关闭您的 PC 上的混合的现实门户应用。</span><span class="sxs-lookup"><span data-stu-id="4997b-126">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="4997b-127">从您的 PC 耳机中拔出。</span><span class="sxs-lookup"><span data-stu-id="4997b-127">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="4997b-128">在命令提示符处运行以下脚本：</span><span class="sxs-lookup"><span data-stu-id="4997b-128">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="4997b-129">重新连接到您的 PC 将耳机。</span><span class="sxs-lookup"><span data-stu-id="4997b-129">Reconnect your headset to your PC.</span></span> <span data-ttu-id="4997b-130">这将使任何已发现的 QR 码"非定位。"</span><span class="sxs-lookup"><span data-stu-id="4997b-130">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="4997b-131">打印代码</span><span class="sxs-lookup"><span data-stu-id="4997b-131">Printing codes</span></span>

<span data-ttu-id="4997b-132">最重要的是，[规范的 QR 代码](https://www.qrcode.com/en/howto/code.html)说"QR 代码符号区域需要边距或"无人参与区域"围绕其可用。</span><span class="sxs-lookup"><span data-stu-id="4997b-132">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="4997b-133">位置，其中会输出任何内容周围符号清除区域。</span><span class="sxs-lookup"><span data-stu-id="4997b-133">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="4997b-134">QR 代码需要在所有边的符号的四个模块宽边距。"</span><span class="sxs-lookup"><span data-stu-id="4997b-134">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="4997b-135">这需要有一个宽度大小的模块-在代码中的一个黑色方块四次，每个侧。</span><span class="sxs-lookup"><span data-stu-id="4997b-135">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="4997b-136">规范的页面包含有关如何打印 QR 代码并找出进行特定大小的 QR 代码所需的区域的建议。</span><span class="sxs-lookup"><span data-stu-id="4997b-136">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="4997b-137">QR 代码检测质量目前易受不同的照明和背景。</span><span class="sxs-lookup"><span data-stu-id="4997b-137">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="4997b-138">若要应对这种情况，请注意你照明并打印将相应的代码。</span><span class="sxs-lookup"><span data-stu-id="4997b-138">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="4997b-139">特别是亮照明场景中打印黑色灰色背景的代码。</span><span class="sxs-lookup"><span data-stu-id="4997b-139">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="4997b-140">在低光场景，黑色白色的工作原理。</span><span class="sxs-lookup"><span data-stu-id="4997b-140">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="4997b-141">同样，如果特别深色背景下的代码，尝试黑色灰色代码上的，如果检测率较低。</span><span class="sxs-lookup"><span data-stu-id="4997b-141">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="4997b-142">否则，如果浅色背景下，常规代码应正常工作。</span><span class="sxs-lookup"><span data-stu-id="4997b-142">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="4997b-143">QRTracking API</span><span class="sxs-lookup"><span data-stu-id="4997b-143">QRTracking API</span></span>

<span data-ttu-id="4997b-144">QRTracking 插件公开 Api，可用于跟踪的 QR 代码。</span><span class="sxs-lookup"><span data-stu-id="4997b-144">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="4997b-145">若要使用该插件，您将需要使用以下类型从*QRCodesTrackerPlugin*命名空间。</span><span class="sxs-lookup"><span data-stu-id="4997b-145">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="4997b-146">实现跟踪在 Unity 中的 QR 代码</span><span class="sxs-lookup"><span data-stu-id="4997b-146">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="4997b-147">示例 MRTK （混合现实工具包） 中的 Unity 场景</span><span class="sxs-lookup"><span data-stu-id="4997b-147">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="4997b-148">您可以找到有关如何使用混合现实工具包中的 QR 跟踪 API 示例[GitHub 站点](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)。</span><span class="sxs-lookup"><span data-stu-id="4997b-148">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="4997b-149">MRTK 已实现所需的脚本，以 simpilify QR 跟踪使用情况。</span><span class="sxs-lookup"><span data-stu-id="4997b-149">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="4997b-150">所有必要资产可开发 QR 跟踪应用程序位于"QRTracker"文件夹中。</span><span class="sxs-lookup"><span data-stu-id="4997b-150">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="4997b-151">有两个场景： 第一种是一个示例，用于检测到它们，以及第二个演示如何使用坐标系统附加到的 QR 代码以显示全息只需显示的 QR 代码的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4997b-151">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="4997b-152">没有预设"QRScanner"添加到在后台使用 QRCodes 的所有必要 scrips。</span><span class="sxs-lookup"><span data-stu-id="4997b-152">There is a prefab "QRScanner" which added all the necessary scrips to the scenes to use QRCodes.</span></span> <span data-ttu-id="4997b-153">脚本 QRCodeManager 是实现 QRCode API 可以将其添加到您的场景的 singileton 类。</span><span class="sxs-lookup"><span data-stu-id="4997b-153">The script QRCodeManager is a singileton class that implements the QRCode API you can add it to you scene.</span></span> <span data-ttu-id="4997b-154">脚本"AttachToQRCode"用于将全息附加到的 QR 码 coodridnate 系统，此脚本可以添加到任何你全息。</span><span class="sxs-lookup"><span data-stu-id="4997b-154">The scripts "AttachToQRCode" is used to attach holograms to the QR Code coodridnate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="4997b-155">"SpatialGraphCoordinateSystem"显示了如何使用 QRCode 坐标系统。</span><span class="sxs-lookup"><span data-stu-id="4997b-155">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="4997b-156">因为是您项目的场景中，可以使用这些脚本也可以编写您自己直接使用的插件上文所述。</span><span class="sxs-lookup"><span data-stu-id="4997b-156">These scripts can be used as is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="4997b-157">实现跟踪而无需 MRTK Unity 中的 QR 代码</span><span class="sxs-lookup"><span data-stu-id="4997b-157">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="4997b-158">您可以不依赖于 MRTK 的情况下在 Unity 中使用 QR 跟踪 API。</span><span class="sxs-lookup"><span data-stu-id="4997b-158">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="4997b-159">若要使用 API，需要准备你的项目使用以下指令：</span><span class="sxs-lookup"><span data-stu-id="4997b-159">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="4997b-160">在名为 unity 项目的 assets 文件夹中创建一个新文件夹："插件"。</span><span class="sxs-lookup"><span data-stu-id="4997b-160">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="4997b-161">从所有所需的文件复制[此文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins)到刚创建的本地"插件"文件夹。</span><span class="sxs-lookup"><span data-stu-id="4997b-161">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="4997b-162">可以使用跟踪中的脚本 QR [MRTK scripts 文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts)或编写自己的。</span><span class="sxs-lookup"><span data-stu-id="4997b-162">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="4997b-163">注意：仅对有这些插件[Windows 10 2018 年 10 月更新 (也称为 RS5)](release-notes-october-2018.md)生成。</span><span class="sxs-lookup"><span data-stu-id="4997b-163">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="4997b-164">将使用下一步的 windows 版本更新插件。</span><span class="sxs-lookup"><span data-stu-id="4997b-164">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="4997b-165">当前的插件是实验性和不能用于 windows 的未来版本。</span><span class="sxs-lookup"><span data-stu-id="4997b-165">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="4997b-166">新插件将发布可从下一个 windows 版本并且它们不会向后兼容和不会使用 RS5）。</span><span class="sxs-lookup"><span data-stu-id="4997b-166">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="4997b-167">实现在 DirectX 中跟踪的 QR 代码</span><span class="sxs-lookup"><span data-stu-id="4997b-167">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="4997b-168">若要在 Visual Studio 中使用 QRTrackingPlugin，您需要将 QRTrackingPlugin 引用添加到.winmd。</span><span class="sxs-lookup"><span data-stu-id="4997b-168">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="4997b-169">您可以找到[受支持的平台所需的文件](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)。</span><span class="sxs-lookup"><span data-stu-id="4997b-169">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="4997b-170">获取坐标系统</span><span class="sxs-lookup"><span data-stu-id="4997b-170">Getting a coordinate system</span></span>

<span data-ttu-id="4997b-171">我们定义了与在左上角快速检测正方形的左上角处的 QR 代码对齐右侧坐标系统。</span><span class="sxs-lookup"><span data-stu-id="4997b-171">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="4997b-172">坐标系统如下所示。</span><span class="sxs-lookup"><span data-stu-id="4997b-172">The coordinate system is shown below.</span></span> <span data-ttu-id="4997b-173">Z 轴指向到文件 （未显示），但在 Unity 中的 z 轴是缺纸和惯用左手。</span><span class="sxs-lookup"><span data-stu-id="4997b-173">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="4997b-174">定义 SpatialCoordinateSystem 对齐如下所示。</span><span class="sxs-lookup"><span data-stu-id="4997b-174">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="4997b-175">可以从使用 API 的平台中获取此坐标系*Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*。</span><span class="sxs-lookup"><span data-stu-id="4997b-175">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![QR 代码坐标系统](images/Qr-coordinatesystem.png) 

<span data-ttu-id="4997b-177">从 QRCode ^ 对象代码，下面的代码演示如何创建一个矩形，并将其放入 QR 坐标系统：</span><span class="sxs-lookup"><span data-stu-id="4997b-177">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

<span data-ttu-id="4997b-178">您可以使用的物理大小创建 QR 矩形：</span><span class="sxs-lookup"><span data-stu-id="4997b-178">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="4997b-179">坐标系统可用于绘制的 QR 代码或将全息附加到的位置：</span><span class="sxs-lookup"><span data-stu-id="4997b-179">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="4997b-180">同时，你*QRCodesTrackerPlugin::QRCodeAddedHandler*可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="4997b-180">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="4997b-181">故障排除和常见问题解答</span><span class="sxs-lookup"><span data-stu-id="4997b-181">Troubleshooting and FAQ</span></span>

<span data-ttu-id="4997b-182">**常规故障排除**</span><span class="sxs-lookup"><span data-stu-id="4997b-182">**General troubleshooting**</span></span>

* <span data-ttu-id="4997b-183">为您的 PC 运行 Windows 10 2018 年 10 月更新？</span><span class="sxs-lookup"><span data-stu-id="4997b-183">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="4997b-184">已设置注册表项？</span><span class="sxs-lookup"><span data-stu-id="4997b-184">Have you set the reg key?</span></span> <span data-ttu-id="4997b-185">之后重新启动设备？</span><span class="sxs-lookup"><span data-stu-id="4997b-185">Restarted the device afterwards?</span></span>
* <span data-ttu-id="4997b-186">QR 代码版本是受支持的版本？</span><span class="sxs-lookup"><span data-stu-id="4997b-186">Is the QR code version a supported version?</span></span> <span data-ttu-id="4997b-187">当前 API 支持最多 QR 代码版本 20 个。</span><span class="sxs-lookup"><span data-stu-id="4997b-187">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="4997b-188">我们建议用于常规用途使用版本 5。</span><span class="sxs-lookup"><span data-stu-id="4997b-188">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="4997b-189">关闭足以 QR 代码？</span><span class="sxs-lookup"><span data-stu-id="4997b-189">Are you close enough to the QR code?</span></span> <span data-ttu-id="4997b-190">照相机越接近 QR 码，可以支持更高版本的 QR 代码版本 API。</span><span class="sxs-lookup"><span data-stu-id="4997b-190">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="4997b-191">**如何关闭需要到 QR 代码来检测它？**</span><span class="sxs-lookup"><span data-stu-id="4997b-191">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="4997b-192">这将取决于 QR 代码的大小，并且也是哪个版本。</span><span class="sxs-lookup"><span data-stu-id="4997b-192">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="4997b-193">对于从 5 cm 边 25 厘米边到不同的版本 1 QR 代码，最小检测距离范围从 0.15 计量到 0.5 米。</span><span class="sxs-lookup"><span data-stu-id="4997b-193">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="4997b-194">最远掉这些可以从检测到会从较小的 QR 代码目标的大约 0.3 指标 1.4 改为适用于更大。</span><span class="sxs-lookup"><span data-stu-id="4997b-194">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="4997b-195">为了比这更大的 QR 代码，您可以评估;大小的检测距离呈线性增加。</span><span class="sxs-lookup"><span data-stu-id="4997b-195">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="4997b-196">我们跟踪程序并不适用于使用边的 QR 代码小于 5 cm。</span><span class="sxs-lookup"><span data-stu-id="4997b-196">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="4997b-197">**使用徽标工作的 QR 代码？**</span><span class="sxs-lookup"><span data-stu-id="4997b-197">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="4997b-198">使用徽标的 QR 代码尚未经过测试，当前不受支持。</span><span class="sxs-lookup"><span data-stu-id="4997b-198">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="4997b-199">**如何清除的 QR 代码从我的应用程序以便它们不会保留？**</span><span class="sxs-lookup"><span data-stu-id="4997b-199">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="4997b-200">在启动会话中，才会保留的 QR 代码。</span><span class="sxs-lookup"><span data-stu-id="4997b-200">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="4997b-201">后重新启动 （或重新启动该驱动程序） 时，它们将进入并为新对象下一次检测到。</span><span class="sxs-lookup"><span data-stu-id="4997b-201">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="4997b-202">QR 代码历史记录在系统级别上保存在驱动程序会话，但您可以将应用配置为忽略早于特定的时间戳的 QR 代码，如果你想。</span><span class="sxs-lookup"><span data-stu-id="4997b-202">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="4997b-203">当前 API 支持清除 QR 代码历史记录，如多个应用程序感兴趣的数据。</span><span class="sxs-lookup"><span data-stu-id="4997b-203">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="4997b-204">**RS5 和未来版本的插件不兼容**RS5 版本的插件仅适用于 RS5，而不能用于将来的版本。</span><span class="sxs-lookup"><span data-stu-id="4997b-204">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="4997b-205">Expermental 插件将替换为实际的插件，应是一个值，我们可以使用在将来版本的 windows。</span><span class="sxs-lookup"><span data-stu-id="4997b-205">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
